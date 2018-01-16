---
layout: page
title: Start contributing
permalink: /start-contributing/
---

<script>
    //you don't want this to be the same as what I need, probably
    var settings = {
            tags: ["beginners", "first-timers-only", "good%20first%20bug", "help%20wanted"],
            organisation: "intermine",
            access_token: "e56559dab5132ef3b8a158cada879db6f752410e"
        },

//////////// YOU PROBABLY DON'T WANT TO EDIT BELOW HERE

        //this var is to keep track of the ids shown on the page
        //so we don't show repeat issues if they have multiple tags
        added = [];

    // thanks mozilla for helping me when I'm too lazy to write basic xhr code
    //https://developer.mozilla.org/en-US/docs/Web/Guide/AJAX/Getting_Started

    //load requests as as soon as the page is ready
    document.addEventListener("DOMContentLoaded", function(event) {
        var httpRequest;

        //map through all tags shown in the settings
        //and make one API call per tag
        settings.tags.map(function(tag) {
            makeRequest(tag)
        });

        //this is where we call the api
        function makeRequest(tag) {
            httpRequest = new XMLHttpRequest();
            //rudimentary error handling
            if (!httpRequest) {
                handleError("Error loading tag: '" + tag + "'");
                return false;
            }
            httpRequest.onreadystatechange = handleResults;
            httpRequest.open('GET', buildURL(tag));
            httpRequest.send();
        }

        //build the url to fetch data for a given org, token, tag combo.
        function buildURL(tag) {
            return 'https://api.github.com/orgs/' + settings.organisation +
                '/issues?access_token=' + settings.access_token +
                '&filter=all&labels=' + tag + '&state=open';
        }

        //cool. Let's go through all result we're given and add them
        // to the screen unless they're already present.
        function handleResults(event) {
            if (event.target.readyState === XMLHttpRequest.DONE) {
                if (event.target.status === 200) {
                    printResults(JSON.parse(event.target.responseText))
                } else {
                    handleError('There was a problem with the request.');
                }
            }
        }

        // given a set of results for a tag, generate html for each one
        // and add to our table.
        function printResults(results) {
            var table = document.getElementById('issues');
            results.map(function(result) {
                if (added.indexOf(result.id) < 0) {
                    table.appendChild(formatResult(result));
                    added.push(result.id);
                }
            });
        }

        //where the actual html generation mentioned above is done
        function formatResult(result) {
            var resultNode = document.createElement("tr");
            resultNode.classList.add("issue");
            //this is lazy but fast to write and sufficient for the job
            resultNode.innerHTML = "<td class='repo-language'>" + result.repository.language + "</td>" +
                "<td class='repo-name'> <a href='" + result.repository.html_url +
                "'>" + result.repository.name + "</a></td>" +
                "<td><a href='" + result.html_url + "'>" +
                result.title + "</a> </td>";
            return resultNode;
        }

        //nothing could ever go wrong, but just in case. :D
        function handleError(errorText) {
            document.getElementById("errors").innerHTML += "<br>" + errorText;
        }

    });
</script>

<table>
    <thead>
        <tr>
            <td>Repo&nbsp;language</td>
            <td>Repo&nbsp;name</td>
            <td>Issue</td>
        </tr>
    </thead>
    <tbody id="issues">
    </tbody>
</table>
<div id="errors"></div>

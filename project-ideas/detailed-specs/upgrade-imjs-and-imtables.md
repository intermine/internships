---
layout: page
title: imjs and im-tables GSoC project
permalink: /project-ideas/2019/detailed-specs/upgrade-imjs-and-imtables
---

## Background:

InterMine results are currently displayed on JSP pages using [im-tables](https://github.com/intermine/im-tables), a [coffeescript](https://coffeescript.org/)-based table displayer. You can read more about the features in the [InterMine user guide](https://flymine.readthedocs.io/en/latest/results-tables/Documentationresultstables.html#results-tables). The communication layer is powered by [imjs](https://github.com/intermine/imjs), also written in coffeescript. 

im-tables was last updated in late 2014 or early 2015, and right now the only way to update it is to install an incredibly old version of node - it won’t build under any modern versions. Your jobs as a GSoC student would be to give these repos some of upgrade love they need and modernise the libraries. 

## Some of the tasks we'd like to address

### Minimum required features

- Upgrade the dependencies for both libraries and ensure tests still pass. 
- The imjs tests are directly coupled with intermine and function more like integration tests than unit tests - without a running local intermine test instance, imjs tests can’t pass. It would be nice to create mock testing objects that we could use instead of a full InterMine. See the [imjs testing docs](https://travis-ci.org/) for more info, as well as [the GitHub issue discussing possible options](https://github.com/intermine/imjs/issues/9).

### Bonus features

- imjs & im-tables are both quite large packages, even minified. They use browserify to convert them from node-ready packages to browser-ready packages. 
    - Maybe we could use Webpack and convert to modern js modules - [import](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/import) & [export](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export)
    - or maybe we can just upgrade browserify! 
- Pure Javascript is probably easier to maintain, and ES2015 supports a lot of the features that made coffeescript popular. It might be nice to use [Decaffeinate](https://github.com/decaffeinate/decaffeinate) to migrate to javascript instead. 
- Better documentation. We have a few examples of imjs in use ([demo](http://intermine.org/imjs/examples/), [code](https://github.com/intermine/imjs/tree/dev/docs/examples)), but it would be nice to add other methods and maybe link to them directly from [our api docs](http://intermine.org/imjs/).
- Any open issues in the GitHub repos. 

## Getting started

1. Get familiar with InterMine and InterMine queries. [We have a Javascript-oriented tutorial](https://hackmd.io/QvITbTCSQkKWYjE2i_Xj_w#) you might like to try first. 
2. Clone [imjs](https://github.com/intermine/imjs) and [im-tables](https://github.com/intermine/im-tables). 
    -  You might want to use [nvm](https://github.com/creationix/nvm) to manage your node version, if you don't already. 
3. Follow the set-up instructions for each repo and take a look through the code. Don't worry if you can't get im-tables to build! It requires a very old version of node. If you really like, you use nvm to try to roll back to an old version of node - maybe v0.10? - and see if that fixes the build. 
4. **Start thinking about your project plan** Use the repos you've installed to explore the features we've discussed above so you can get a feeling for the things we'd like you to address. How long do you think each task might take and what would your preferred approach be? 

## Need help? Questions? 

Try asking in the GSoC chat. The mentors for this project are:

-  Yo Yehudi
-  Aman Dwivedi

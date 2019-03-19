---
layout: page
title: Datavis GSoC project
permalink: /project-ideas/2019/detailed-specs/js-data-vis
tags: intermine, gsoc
---

# DataVis project

InterMine provides large amounts of data, and we'd like to add some more data visualisation tools to our new user interface. Some possible examples might be:

 - Expression graphs, such as:
     - [a replica of the expression graphs in FlyMine](http://www.flymine.org/flymine/portal.do?class=Gene&externalids=FBgn0004053#expression)
     - [an expression heatmap](https://github.com/ebi-gene-expression-group/atlas-heatmap)
 - Visualisations similar to [the ones found in our python client](https://github.com/intermine/intermine-ws-python-docs/blob/master/14-tutorial.ipynb)
 - [BioJS MSA viewer](https://github.com/wilzbach/msa)
    - This would show on a gene list page and pass FASTA sequences for each gene to the msa viewer. FASTA for lists is available via the [web services](http://iodocs.apps.intermine.org/). 
 - a [3d Protein visualiser](https://www.npmjs.com/package/bio-pv)
    - Most InterMines don't have pdb ids associated with their proteins. This can be fetched via [the PBD search REST API](http://www.rcsb.org/pages/webservices/rest-search#search). Once the pdb id is determined the pdb files can be downloaded from the [PDB download service](http://www.rcsb.org/pages/download/http#structures), and then passed to the visualiser. 
 - [Volcano plots](https://en.wikipedia.org/wiki/Volcano_plot_(statistics))
 - [Manhattan plots](https://en.wikipedia.org/wiki/Manhattan_plot)
 - [Box plots](http://www.physics.csbsju.edu/stats/box2.html)
 - [Violin plots](https://en.wikipedia.org/wiki/Violin_plot)
 - Combining [Swarm plots](https://bl.ocks.org/mbostock/6526445e2b44303eebf21da3b6627320) and [Box plots](http://www.physics.csbsju.edu/stats/box2.html)

[biojs.net](http://biojs.net) is a good source for more visualisation libraries.

## Background

The current InterMine interface is powered by JSPs (example: [http://www.flymine.org](http://www.flymine.org)) and will be discontinued in the next few years. We're building a new interface, code-named [BlueGenes](https://github.com/intermine/bluegenes/) ([Live demo](http://bluegenes.apps.intermine.org/)). We want to make it extra easy for people to port their existing javascript tools into BlueGenes, so we've created a set of specifications to allow javascript applications to interact with BlueGenes. This is known as the BlueGenes Tool API. You can read more about this on [our Tool API release blog announcement](https://intermineorg.wordpress.com/2018/12/03/javascript-everywhere-the-bluegenes-tool-api-version-1-is-released/).

## Getting started

1. Take some time to learn more about InterMine and InterMine queries. Take a look through [Getting started with InterMine JS-Based applications](https://hackmd.io/QvITbTCSQkKWYjE2i_Xj_w#).
2. Okay, now we have the basics down, let's take a look at an existing visualisation. Visit a [report page in FlyMine](http://www.flymine.org/flymine/portal.do?class=Gene&externalids=FBgn0004053#interactions) and scroll down to the interaction network viewer. This is one example of a data visualisation where we use data from InterMine that has also been ported to BlueGenes. To see the same visualisation in [BlueGenes](http://bluegenes.apps.intermine.org/), search for "FBgn0004053" and go to the first result page.
3. Now let's have a quick look at the code for the interaction network viewer:
    - Source code: https://github.com/intermine/cytoscape-intermine - take a look at index.html to see how the visualiser is initialised
    - To include it in bluegenes, we've added a thin wrapper around the cytoscape-intermine repo - check out https://github.com/intermine/bluegenes-tool-cytoscape - you'll see it doesn't have much code at all!
4. Take the [BlueGenes Tool API Tutorial](https://github.com/intermine/bluegenes/blob/dev/tools/docs/tool-api-tutorial.md). The yeoman generator in the tutorial was used to convert the network viewer into a bluegenes compatible tool. Go back to https://github.com/intermine/bluegenes-tool-cytoscape and have a look through the files now that you've completed the tutorial. It should look more familiar!
5. **Time to think about the project proposal**: if you've made it this far, hopefully you have an understanding of the technical requirements to make a BlueGenes data visualisation. Pick a few of the possible visualisations that interest you and start to prepare a project plan.      How long do you think each task might take and what would your preferred approach be? You can discuss this with mentors and/or start writing your proposal. Always share our proposal drafts with your mentors so they can offer feedback, and take a look through [our advice for applications](http://intermine.org/gsoc/guidance/students-applying/) to find tips and a proposal template.

## Need help? Questions?

Try asking in the GSoC chat. The mentors for this project are:

- Yo Yehudi
- Adrián Rodríguez-Bazaga
- Aman Dwivedi

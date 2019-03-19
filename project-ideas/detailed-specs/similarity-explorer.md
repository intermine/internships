---
layout: page
title: Similarity explorer tool
permalink: /project-ideas/2019/detailed-specs/similarity-explorer
tags: intermine, gsoc
---

# InterMine Similarity Explorer


## Background
InterMine allows scientists to explore biological data. One topic that might be of interest to research scientists would be to use explorative data visualisation to identify previously unknown similarities between two different biological objects (this could be genes, proteins, or other entities).

In order to enable this, we would like to make an explorable graph visualisation of the relationships between InterMine entities. 

The current InterMine interface is powered by JSPs (example: [http://www.flymine.org](http://www.flymine.org)) and will be discontinued in the next few years. We're building a new interface, code-named [BlueGenes](https://github.com/intermine/bluegenes/) ([Live demo](http://bluegenes.apps.intermine.org/)). This tool should be designed to work as a visualisation / tool embedded in BlueGenes _and_ as a standalone tool as well.
This is known as the BlueGenes Tool API. You can read more about this on [our Tool API release blog announcement](https://intermineorg.wordpress.com/2018/12/03/javascript-everywhere-the-bluegenes-tool-api-version-1-is-released/).

## Project goal: 
Build a javascript based tool designed to sit on BlueGenes list pages (e.g. a page with a list of Genes or a list of Proteins). 
### Specifications 
- Two main UI components, a graph visualisation and filters to control it: 
    - **Graph**: A [cytoscape.js](http://js.cytoscape.org/)-based graph, which visualise interactions between objects in an InterMine list, with each gene (or protein) shown as a node, and interactions represented as an edge. 
        - If the items on the list don't interact, the nodes should float freely, unattached to any other nodes.
    - **Filters**: The filters in question need to look at other aspects of the data for each node and allow users to adjust the appearance of the nodes depending in the data values. For example, if a given gene was highly upregulated in the pancreas, it might have a thick yellow border, and if it was downregulated it might instead have a border that's blue. 
        - Some of the other ways we might modify nodes based on the associated data:
            - Node colour
            - Node border border colour
            - Node border style
            - Node fill style.
        - When filters update, the graph should adjust seamlessly rather than completely re-drawing. 
        - All colour-based attributes should be from a [colourblind-friendly palette](http://colorbrewer2.org/#type=diverging&scheme=BrBG&n=3). ([why this is important](https://venngage.com/blog/color-blind-friendly-palette/))

## Getting started

1. Foundational knowledge: Take some time to learn more about InterMine and InterMine queries by looking through [Getting started with InterMine JS-Based applications](https://hackmd.io/QvITbTCSQkKWYjE2i_Xj_w#).
4. Take the [BlueGenes Tool API Tutorial](https://github.com/intermine/bluegenes/blob/dev/tools/docs/tool-api-tutorial.md). The yeoman generator in the tutorial was used to convert the network viewer into a bluegenes compatible tool. Go back to https://github.com/intermine/bluegenes-tool-cytoscape and have a look through the files now that you've completed the tutorial. It should look more familiar! 
5. **Time to think about the project proposal**: if you've made it this far, hopefully you have an understanding of the technical requirements to make a BlueGenes data visualisation. Pick a few of the possible visualisations that interest you and start to prepare a project plan.      How long do you think each task might take and what would your preferred approach be? You can discuss this with mentors and/or start writing your proposal. Always share our proposal drafts with your mentors so they can offer feedback, and take a look through [our advice for applications](http://intermine.org/gsoc/guidance/students-applying/) to find tips and a proposal template.

## Need help? Questions?

Try asking in the GSoC chat. The mentors for this project are:

- Yo Yehudi
- Adrián Rodríguez-Bazaga
- Aman Dwivedi

---
title: Software Zero - Minimum Viable Product
author: Harlan Knight Wood, Jack Senechal, Travis Wellman
layout: post
---

Software Zero is:

 * [ForkDiffMerge][] with enough navigable data visualization to make sense of the trees of remixes in your communities of trust.
 * The enlightened technology platform in which to crowdsource all the other enlightened technology platforms.
 * A foundation for the full systems -- we have in mind the full-blown vision, and we want to do steps towards that.
 * Composed of thin components which communicate over well-defined HTTP interfaces.

The MVP must be good enough that people want to use it, and keep coming back. 

Assumptions
===========
Publishing
  : People publish their websites however they choose, eg Wordpress, Jekyll, wikis, etc.

NodeCollective
==============
User can register (eg) nanotechdesertsolar.com as a NodeCollective -- 
which in turn allows users to register nanotechdesertsolar.myname.com as a nanotechdesertsolar fork.  
The parent collective has datavis / datanav of the viewer's trust networks' flowerings of relevant nodes.

Dataviz / Datanav
-----------------

 * View the node collection that is the intersection between this node collective (eg “nanotechdesertsolar”) and the viewer's trust network
 * Radial node network interface
 * Navigate the node collections' radial node/edge interface
 * One node is central, surrounded by nodes of interest to the viewer -- "related" through topic, trust metrics, etc
 * When you click on a node, it zooms into full view (ie you are on that "page" or node), but navigation is still present around the edges, eg the network is present but compressed around the edges, or hints of the network are present

Trust Filters
-------------
User trust ratings of nodes (primarily including authors and content)
Basic trust cone algorithms to apply the trust information in a meaningful way

Remixing
========
Authors can drop in JavaScript snippet to make a fork button on their page, and show other available forks (through NodeCollective)

MergeChanges
============
Users submits documents to compare, and a diff is displayed.

Merging is an interactive process that happens on the client side, in the diff tool. The resulting document can be saved to the node store.

BaseParadigm
============
At a low level, everything rests on node stores and graph edges.



[ForkDiffMerge]: /ForkDiffMerge
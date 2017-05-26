---
layout: post
title:  "Week 0: Introduction"
date:   2017-05-12 00:41:49 +0530
---
I am [Kartik Patel][home], final year student at Indian Institute of Technology Roorkee. I am student participant at Google Summer of Code 2017 in the organization [GNU Radio][gnuradio]. I am working on a web based display for GNU Radio. The detailed introduction and details of the project is available in [my proposal][proposal]. I will be mentored by [Sebastian Koslowski][sebastian].

#### Comunication with Community
The code of whole module is available on Github at [this link][repo]. I plan make frequent additions to the code in order to complete the tasks as planned. The weekly updates of my tasks will be published on this blog on every Friday. Also, a short email with a brief details and link to the blog will be sent to the GNU Radio [discussion forum][discussion_forum] for the reference. For any query or feedback regarding the module, kindly send me an email at [kartikpatel1995@gmail.com][email] with [discuss-gnuradio@gnu.org][discussion_forum] in CC.

#### Using the module
The module repository has two branches. 
1. <b>master</b>: A stable code. Every feature once developed and tested will be merged to the <b>master</b> branch. At any instant, the master branch will allow the user to use and test the module with implemented features.
2. <b>develop</b>: A development branch: This will be a branch having most recent version of code. This branch will be used to push all the code during the development. It does not gaurantee a complete bug free code. (No one can gaurantee an <i>absolute bug free code</i> though!)

#### Task for Week 0
The tasks for Week 0 is grouped as follows:
1. <b>Defining the workflow of module</b>: Defining minute details like when the Bokeh server is initiated, when the Bokeh server connects the streams, when the client should call the the server for the data etc.
1. <b>Redifining and optimizing the structure and dataflow of the module</b>: The proposal does not have an optimized approach of streaming the data to client. We have to figure out an optimized way of streaming data considering boundary cases like slow or broken connections. One approach is somehow having a fast processing of the data (preferably using C++) and connecting it with a Python function which will be called by the Bokeh server for streaming. Hence, googling about other approaches and possible implementational details will be carried out.
2. <b>In depth understanding of the [Bokeh][bokeh] library</b>: Since, this library is fundamental requirement of the prject, a detailed structured understanding of the library will be carried out. 
3. <b>Defining milestones of the project</b> in order to quantify the progress of the project.


This concludes the tasks for Week 0. A brief introduction about me and the module was added. I also added my way of being in touch with the organisation.

[home]: /
[gnuradio]: https://gnuradio.org
[proposal]: /GSoC2017/BokehGuiForGNURadio.pdf
[bokeh]: http://bokeh.pydata.org/en/latest/
[sebastian]: https://github.com/skoslowski
[repo]: https://github.com/kartikp1995/gr-bokeh/
[email]: mailto:{{ site.email }}
[discussion_forum]: mailto:discuss-gnuradio@gnu.org

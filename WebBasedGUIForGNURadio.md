# GSoC 2017: Web based GUI for GNU Radio applications

## Introduction
Web based GUI are becoming more famous(used to, widespread) because of easy to use and easy to view outputs. Currently GNU Radio works on a standalone system (many times connected to a hardware). The output of GNU Radio is displayed using QT GUI framework. In addition to that, various input widgets of QT framework are used to interact with the ongoing simulations. The QT framework allows the input/output operations only from the system running the simulation.

In this project, an OOT module for web based GUI is proposed for GNU Radio. The primary focus of the project will be an output mechanism which will enable the output viewing through the web portal. In addition to the output mechanism, interactive HTML inputs will be used to iteract with the ongoing simulations.

### Major features of the project
1. Alternative output mechanism other than Python QT framework
2. Allow real-time interaction with the program remotely
3. Simultaneous real-time multi-user interaction with the program

## Proposed mechanism and comparison with `gr-qtgui`
At present, GNU Radio plots various figures in dialog box based on QT Framework. Similarly, the proposed module will show various figures through HTML page served from the system running the simulations. In particular, we will use [`Bokeh` library](http://bokeh.pydata.org/en/latest/) to setup the server, sessions, documents and plots. Figure 1 provides comparison of proposed mechanism with the current structure.

![Figure 1: Comparison of `gr-qtgui` with `gr-webgui`](WebGui/fundamental.png "Figure 1: Comparison of `gr-qtgui` with `gr-webgui`")

On the client side, a web browser requests a page from `server:port/?session-id=session_id`. The server sends the *Document* object corresponding to the session identified by `session_id`. Since, there is only one Document and session instance on server, all web browsers receives same Document instance. Hence, changing the parameters or plot configurations will ensure the change in all clients viewing the document.

## The suggested features
A summary of suggested features are as follows:

1. Following plots will be implemented for the web based GUI. Most plots are directly available in Bokeh library. Others can be developed by providing the formatted input values to existing plots in Bokeh library.
   - Constellation Display
   - Histogram Display
   - BER Sink
   - TimeRaster Display
   - Frequency Display
   - Time Display
   - Waterfall Display

2. Following input widgets will be implemented for the web based GUI. All these widgets are already available in Bokeh library.
   - Checkbox
   - Chooser (Drop-down menu in HTML)
   - TextBox
   - Label (Non-editable textbox)
   - Push Button
   - Range Slider
   - Slider
   - Tab Panes

3. Add GRC blocks for the Sinks
   - Add option in _Options_ block and define building of _top_block.py_
   - Add GRC blocks for each sinks and input widgets mentioned above

Finally, an OOT module is to be developed. Upon changing the _Options_ block in GRC, web based GUI will be enabled and hence, a server process will be initiated. Opening the URL from web browser will show the expected plots and input widgets.

## Proposed work during GSoC 2017
The miniature version of whole implementation is available [here](https://github.com/kartikp1995/gr-htmlgui/). The file [_time_sink_f.py_](https://github.com/kartikp1995/gr-htmlgui/blob/master/python/time_sink_f.py) implements basic sink for floating point input and the file [_top_block.py_](https://github.com/kartikp1995/gr-htmlgui/blob/master/examples/top_block.py) is an example on how the sinks will be used. You can review the output [here](http://terminal.kartikpatel.in:5006/?bokeh-session-id=ARfUOyu0urukFhh3TmXRqHari59Bo1w2O4GGnseztvCL).

Proposed flow of the OOT module `gr-webgui` is explained below.
- Need to finalize it as soon as possible.

## Timeline


## Personal background and previous experience
I am final year undergraduate student at Department of Electronics and Communication Engineering, Indian Institute of Technology Roorkee. I will be joining ____ for Ph.D. in Electrical and Computer Engineering with majors in Electrical Engineering. My area of interests revolve around Communication systems and I have developed web and software development as my hobby. My major motivation to apply to GSoC 2017 is to get involved in GNU Radio development. Since, registration for my graduate studies are generally in beginning of September, I will be mostly available for the duration of May-August except 3-4 days sometimes in June or July to complete my visa process.

My experience in programming and in particular open-source development is as follows:
- __Implementation of Bluetooth Low Energy module in NS3__ [\[Link\]](https://github.com/kartikp1995/ns-3-dev-git/) - Designed and implemented Bluetooth Low Energy protocol stack in NS3. Initially developed the basic idea [here](https://github.com/kartikp1995/ns-3-dev-git/wiki/Development-of-BLE) and then implemented whole module within 4 weeks.

- __Chief Technical Lead, Information Management Group (IMG), IIT Roorkee__ - IMG develops and maintains the IIT Roorkee Intranet & Internet systems. We manage the Institute website, Content Management System, Placement Portal and many other applications for the institute. I am responsible for all aspects of the backend stack including performance management and security. I initiated changes in development cycle to optimize the resource usage of servers and reduce the frequency of communication between servers and databases.

- In the beginning of 2017, I attempted to contribute to GNU Radio in order to get familiarize with organization and codebase. Following are my attempts to contribute to the code.
  - Created the pull request with the feature to _Duplicate flowgraph_ and _Save a Copy_ (PR: [#1188](https://github.com/gnuradio/gnuradio/pull/1188)).
  - Solved issue [#1124](https://github.com/gnuradio/gnuradio/issues/1124)
  - Solved issue [#1192](https://github.com/gnuradio/gnuradio/issues/1192)

## Secret codewords
Cyberspectrum is the best spectrum.

## Conclusion
An overview of the module for web based GUI for GNU Radio is given in the previous sections. With example of a small scale implementation, the flow of development is explained. The project is devided into proper timeline so that mentor and community can track the progress of the project.


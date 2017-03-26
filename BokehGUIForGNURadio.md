# GSoC 2017: Web based GUI for GNU Radio applications

## Introduction
Currently GNU Radio works on a local system (many times connected to a hardware). The display of GNU Radio is displayed using QT GUI framework. In addition to that, various input widgets of QT framework are used to interact with the ongoing simulations. The QT framework contrains the input/output operations from the system running the simulation.

In software development, the new paradigm is moving towards web based systems because of simple usability for the user and wide range of available frameworks for developers. In this project, an OOT module for web based GUI is proposed for GNU Radio. The primary focus of the project will be an display mechanism which will be used to interact with ongoing simulation based on the parameters provided through interactive HTML inputs.

In the proposal, the focus is on the flow of the final OOT module and implementational details. The details of minute tasks like arrangement of plots & widgets inside the output, the color and labeling of the plots etc. have been intentionally left out but will be implemented taking QT GUI as guideline.

### Advantages of the project
1. Alternative output mechanism other than Python QT framework
2. Allow real-time interaction with the program remotely
3. Simultaneous real-time multi-user interaction with the program
4. Flexible module to incorporate the future development in direction web-based software

## Proposed mechanism and comparison with `gr-qtgui`
At present, GNU Radio plots various plots in the window based on QT Framework. Similarly, the proposed module will show various plots through HTML page served from the system running the simulations. In particular, [`Bokeh` library](http://bokeh.pydata.org/en/latest/) will be used to setup the server, sessions, documents and plots. The figure below provides comparison of proposed mechanism with the current structure.

![Figure 1: Comparison of `gr-qtgui` with `gr-webgui`](WebGui/fundamental.png "Figure 1: Comparison of `gr-qtgui` with `gr-webgui`")

On the client side, a web browser requests a page from `server:port/?session-id=session_id`. In response to the request, the server sends the *Document* object corresponding to the session identified by `session_id`. Since, there is only one Document and session instance on the server, all web browsers receives same Document instance. Hence, changing the parameters or plot configurations will ensure the change is displayed to all clients viewing the document.

## The proposed features
A summary of proposed features are as follows:

1. Following plots will be implemented for the web based GUI. Most plots are directly available in Bokeh library. Others can be developed by providing the formatted input values to existing plots in Bokeh library.
   - Constellation Sink
   - Histogram Sink
   - BER Sink
   - Frequency Sink
   - Time Sink
   - Waterfall Sink
   - TimeRaster Sink (If time permits)

2. Following input widgets will be implemented for the web based GUI. All these widgets are already available in Bokeh library.
   - Checkbox
   - Chooser (Drop-down menu in HTML)
   - TextBox
   - Label (Non-editable textbox)
   - Push Button
   - Range Slider
   - Slider
   - Tab Panes

3. GRC integration
   - Add option in _Options_ block and define building of _top_block.py_
   - Add GRC blocks for each sinks and input widgets mentioned above

Finally, an OOT module is to be developed. Upon changing the _Options_ block in GRC, web based GUI will be enabled and hence, a server process will be initiated. Opening the URL from web browser will show the expected plots and input widgets.

## Proposed work during GSoC 2017
The working prototype of entire project is available [here](https://github.com/kartikp1995/gr-htmlgui/). The file [_time_sink_f.py_](https://github.com/kartikp1995/gr-htmlgui/blob/master/python/time_sink_f.py) implements basic sink for floating point input and the file [_top_block.py_](https://github.com/kartikp1995/gr-htmlgui/blob/master/examples/top_block.py) is an example on how the sinks will be used. You can review the output [here](http://terminal.kartikpatel.in:5006/?bokeh-session-id=ARfUOyu0urukFhh3TmXRqHari59Bo1w2O4GGnseztvCL).

In the sample program, only Python is used to develop the idea. But in general, Python is much slower than C++. Hence, the OOT module will have both Python and C++ code as structured in figure below. Python will be used to interact with the plots and other blocks and C++ will be used to pre-process the data before sending to the plots.

![Figure 2: Proposed structure and flow of the program](WebGui/structure.png "Figure 2: Proposed structure and flow of the program")

1. __sink_impl__ : C++ class which will be inherited. Contains functions related to processing of the data.
2. __sink__ : Python class inherited from __sink_impl__ class containing methods to configure and communicate with the plots. All processing of the data will be done in functions of __sink_impl__.
3. __widgets__ : Bokeh provides all required input widgets with appropriate mechanism for javascript as well as backend callbacks. Hence, this class will take care of all such widgets and their corresponding python callback functions.
4. __forms/toolbars__ (If time permits) : The group of widgets that forms a toolbar. For an instance: in frequency plots, one can have a range slider for the range of frequency of interest, button for "autorange" and similarly more. Grouping all these makes the system modular and easy to extend.

Note: The _sink_impl_ and _sink_ is a generic term to point all sinks. e.g. in case of floating point time sink, it will be __time_sink_f_impl__ and __time_sink_f__.


Based on this, overall flow of the OOT module `gr-webgui` is as follows:
- _top_block.py_ initialize the server, session, doc and sinks.
- The sinks have instance of the corresponding doc, and initialises plot.
- The _work()_ function process the _input_items_ and stream the _output_items_ to the plot.

Please note that, at present, it is considered that the output plots are displayed on the same system or on the small network. In other words, the application for the output over the Internet is not considered for now. Hence, it can be safely assumed that the samples will not be required to be dropped. Also, during streaming of the data, re-streaming will not be necessary.

## Timeline
The timeline provided by Google suggests a 1 month of community bonding period. But since, the registration for graduate studies at ___ are around end of August, I will be available for the duration of May-August except 3-4 days sometimes in June or July to complete my visa process. Although I will keep on contributing to GNU Radio, I would like to start coding from 20th May (10 days earlier than suggested date), so that the three month duration ends at 20th August to avoid any loss of work during the registration process at the University.

The necessary documentation will be done in parallel to to the development.
My tentative GSoC timeline is given below:
- __Week 1__ :
  - Initial setup: Define "Generate Options" for Web GUI
  - Complete coding _time_sink_f_impl.cc_
  - Work on time sink for float inputs
- __Week 2__ :
  - Complete time sink for float inputs
  - Conclude Time sink for complex inputs
  - Create GRC block for Time Sink
- __Week 3__ :
  - Add python and GRC example for time sink
  - Complete input widgets: _label_ and _textbox_
  - Define GRC blocks
- __Week 4__ :
  - Complete frequency sink
- __Week 5__ :
  - Add GRC block for frequency sinks
  - Add python and GRC example for frequency sink
  - Start Constellation sink
- __Week 6__ :
  - Complete Constellation sink
  - Add GRC block for Constellation sink
- __Week 7__ :
  - Add python and GRC example for Constellation sink
  - Complete BER sink
  - Add GRC block for BER sink
- __Week 8__ :
  - Add python and GRC example for BER sink
  - Conclude Checkbox and add GRC block
  - Conclude Chooser (dropdown) and add GRC block
- __Week 9__ :
  - Conclude Push Button and add GRC block
  - Conclude slider and add GRC block
- __Week 10__ :
  - Conclude range slider and add GRC block
  - Conclude tab pane and add GRC block
- __Week 11__:
  - Complete waterfall sink
  - Add GRC block for waterfall sink
  - Add python and grc example for waterfall sink
- __Week 12__ :
  Conclude the project <br>
  If time permits: Create a common GRC block for sinks where including one block will show time sink, frequency sink and waterfall sink


## Personal background and previous experience in programming
I am a final year undergraduate student at Department of Electronics and Communication Engineering, Indian Institute of Technology Roorkee. I will be joining ____ for Ph.D. in Electrical and Computer Engineering with majors in Electrical Engineering. My area of interests revolve around Communication systems and I have developed web and software development as my hobby.

Note: ___ is the name of the university which I will be joining but not decided.

My experience in programming and in particular open-source development is as follows:
- __Implementation of Bluetooth Low Energy module in NS3__ [\[Link\]](https://github.com/kartikp1995/ns-3-dev-git/) - Designed and implemented Bluetooth Low Energy protocol stack in NS3. Initially developed the basic idea [here](https://github.com/kartikp1995/ns-3-dev-git/wiki/Development-of-BLE) and then implemented the module within 4 weeks.

- [__Chief Technical Lead, Information Management Group (IMG), IIT Roorkee__](http://img.channeli.in) - IMG develops and maintains the IIT Roorkee Intranet & Internet systems. We manage the Institute website, Content Management System, Placement Portal and many other official applications for the institute.
   - I am responsible for all aspects of the backend stack including performance management and security.
   - Initiated changes in development cycle to optimize the resource usage of servers and reduce the load on servers and databases.
   - Develped and maintained the official placement portal of the institute containg more than 20,000 lines of codes. The student side interface which includes company information, application details and the interface for placement office which includes contact manager and related administrative tasks were developed based on Python/Django framework.

- Since January 2017, I contributed to GNU Radio in order to get familiarize with organization and codebase. Following are my contributions to the code.
  - Pull request with the feature to _Duplicate flowgraph_ and _Save a Copy_ (PR: [#1188](https://github.com/gnuradio/gnuradio/pull/1188)).
  - Pull request with the change `cout` to `gr::logger` (PR: [#1178](https://github.com/gnuradio/gnuradio/pull/1178))
  - Solved issue [#1124](https://github.com/gnuradio/gnuradio/issues/1124): Added plot configuration options for Line2 in case of input type `Complex Messages` in QT GUI Time Sink block.
  - Solved issue [#1192](https://github.com/gnuradio/gnuradio/issues/1192): Removed redundant configuration options in QT GUI Time Sink block.

## Secret codeword
Cyberspectrum is the best spectrum.

## Conclusion
An overview of the module for web based GUI for GNU Radio is given in the previous sections. With example of a small scale implementation, the flow of development is explained. All tasks are divided into proper timeline so that mentor(s) and community can track the progress of the project.


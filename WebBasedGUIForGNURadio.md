# GSoC 2017: Web based GUI for GNU Radio applications

## Introduction
Web based GUI are becoming more famous(used to, widespread) because of easy to use and easy to view outputs. Currently GNU Radio works on a standalone system (many times connected to a hardware). The output of GNU Radio is displayed using QT GUI framework. In addition to that, various input widgets of QT framework are used to interact with the ongoing simulations. The QT framework allows the input/output operations only from the system running the simulation.

In this project, an OOT module for web based GUI is proposed for GNU Radio. The primary focus of the project will be an output mechanism which will enable the output viewing through the web portal. In addition to the output mechanism, interactive HTML inputs will be used to iteract with the ongoing simulations.

### Impact of the project
1. Alternative output mechanism other than Python QT framework
2. Allow real-time interaction with the program remotely
3. Simultaneous real-time multi-user interaction with the program

## Current structure and proposed mechanism
At present, GNU Radio plots various figures in dialog box based on QT Framework. Similarly, the proposed module will show various figures through HTML page served from the system running the simulations. In particular, we will use [`Bokeh` library](http://bokeh.pydata.org/en/latest/) to setup the server, sessions, documents and plots. Figure 1 provides comparison of proposed mechanism with the current structure.

![Figure 1: Comparison of `gr-qtgui` with `gr-webgui`](WebGui/fundamental.png)

On the client side, a web browser requests a page from `server:port/?session-id=session_id`. The server sends the *Document* object corresponding to the session identified by `session_id`. Since, there is only one Document and session instance on server, all web browsers receives same Document instance. Hence, changing the parameters or plot configurations will ensure the change in all clients viewing the document.

## The suggested features


## Proposed work during GSoC'17


## Timeline


## Personal background and previous expereince


## Secret codewords
Cyberspectrum is the best spectrum.


## Conclusion



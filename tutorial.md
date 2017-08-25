---
layout: page
title: "Tutorial"
permalink: /tutorial/
---

## Objectives
- Setting up the `gr-bokehgui` and quick preview
- Learn how to use Bokeh GUI sinks
- Learn how to use widgets
- Placement of the elements on the page

## Prerequisite
- Understanding of basic GNU Radio
- Able to use GRC (i.e. [Guided Tutorial GRC][guided_tutorial])

## 1. Setting up the module
The code for the `gr-bokehgui` is available [here][codebase].

### 1.1 Cloning the repository
To begin, we need to clone the git directory. Type following commands in the Terminal
```bash
$ git clone https://github.com/kartikp1995/gr-bokehgui.git
```

### 1.2 Installing the module
Go to cloned repository and run following commands to make and run the module.
```bash
$ mkdir build
$ cd build
$ cmake ../
$ make
$ sudo make install
$ sudo ldconfig
```

To verify if the module is installed correctly, you can run the following command and check if all tests are successful.
```bash
$ make test
```

### 1.3 Quick preview
To preview the module, run any example from `examples/` folder of the module. You can open .grc files using GRC or simply run the Python examples directly from the terminal.

Let's see the output of `examples/tutorial.grc`. Open the file in GRC. Click on Build and Execute.

The following message should be displayed in following Terminal section of GRC window:
```bash
1. 2017-08-24 18:32:35,228 Starting Bokeh server version 0.12.6 (running on Tornado 4.4)
2. 2017-08-24 18:32:35,229 Host wildcard '*' will allow websocket connections originating from multiple (or possibly all) hostnames or IPs. Use non-wildcard values to restrict access explicitly
3. 2017-08-24 18:32:35,240 Starting Bokeh server on port '5006' with applications at paths ['/bokehgui']
4. 2017-08-24 18:32:35,240 Starting Bokeh server with process id: 16229
5. 2017-08-24 18:32:35,652 WebSocket connection opened
6. 2017-08-24 18:32:35,653 ServerConnection created
```

In this message, there are 3 things to look out for: `*` on line 3, `5006` and `/bokehgui` on line 4.

The `5006` is the port on which the Bokeh server is working. `/bokehgui` is the page that shows the application that you open. `*` means that you can open this page from the network using any IP/server name. To view the output from own system: Open the following URL in the browser.

[`http://localhost:5006/bokehgui?bokeh-session-id=tutorial`][link]

We will shortly see where the session-id comes from.

You should see following output on the screen.<br>
![Tutorial Output]({{ site.url }}/{{ site.baseurl}}/images/tutorial/tutorial.png){:width="75%"}

## 2. Using the sinks
First of all, to use Bokeh GUI, we will need to update the properties of the  *Options Block*. Create a new GRC file, double click on *Options Block* update the parameters as shown below:<br>
![Options block]({{ site.url }}/{{ site.baseurl}}/images/tutorial/options.png)<br>
Major things to note here are following:
1. **ID**: This ID is generally the name of the Python file to be generated. In Bokeh case, it is also an ID to view the output. The `bokeh-session-id` parameter in the URL takes this value to distinguish the different simulation processes.
2. **Generate Options**: Make sure you select **Bokeh GUI** in the dropdown menu. It ensures the required program will be added when we build the flowgraph. If you can not find the `Bokeh GUI` option, please make sure you have recent version of the GNU Radio installed.
3. **Widget Placement**: The *placement* parameters in all Bokeh GUI sink blocks and the *Widget Placement* parameter in here help in re-arranging the items which are going to be displayed. Defining *placement* parameters will be explained later in the tutorial.

Now, let's create a simple flowgraph as follows:<br>
![Step 1: Create a Flowgraph]({{ site.url }}/{{ site.baseurl}}/images/tutorial/time_sink_fg.png)<br>
We see that the Time Sink block has an error in the configuration. Opening the properties, we see that we need to provide the `placement` parameter in order to build the Python file. Let's provide `(1,0)` in `placement` parameter.

To see the output, build, run and open the browser.

You can add waterfall sink, frequency sink, constellation sink as required.

Let's add waterfall sink. Use `(2,0,1,2)` when asked for placement parameter. Similarly, add frequency sink and use `(0,1,2,1)` as placement parameter. You can build and execute the flowgraph to start the server. Open the browser to preview the output!

## 3. Using widgets
Now, let's add widgets. We will add a slider that will control noise power, source frequency, and signal amplitude.

First, find a block called _Bokeh GUI Slider_ from the library. Double click the block to configure as follows:<br>
![Slider config]({{ site.url }}/{{ site.baseurl}}/images/tutorial/noise_amp_slider.png)<br>

The most important parameter to note is **ID**. It defines the variable name. Each time slider updates its value, the variable called `frequency` will be changed. Also, it will call a function `set_frequency` as a callback handler.

Now, to incorporate the appropriate callback functions in `set_frequency` function, change the signal source frequency value from a numerical to a variable `frequency`. GRC considers the variable entry and updates the corresponding function of the block to `set_frequency` function. For more details on this, checkout section 2.3 of [Guided Tutorial][guided_tutorial].

Similarly, add `noise_amp` and `signal_amp` sliders in the flowgraph. Edit the Signal source and noise source blocks and update it to the appropriate variable instead of exact values in parameter textbox.

After everything is done, you will see the following flowgraph on the screen.<br>
![Flowgraph]({{ site.url }}/{{ site.baseurl}}/images/tutorial/tutorial.grc.png)<br>

The flowgraph is also available at `examples/tutorial.grc`.

To see it live, build, execute and open the URL in the browser! You will see the output similar to the one shown at the beginning of the tutorial.

## 4. Placement the widgets and plots
We will now focus on placements of the plots and Widgetbox. To clear out things, let's understand how the grid layout is defined in the module.

First of all, to reduce the effort of arranging the widgets individually, a Widgetbox is defined which contains all widgets. The user can arrange Widgetbox just like the plots.

The placement parameters  can have a vector of integers of length 4 of the form `(row, col, rowspan, colspan)`. `(row, col)` is the coordinates of the top-left corner of the element. The `rowspan` and `colspan` correspond to height and width of the element. All values of the row, col, rowspan, and colspan are in terms of the number blocks.

The following figure is an example of the grid, the placements of various elements inside the grid for the given value of parameters. <br>
![GridPlot Example]({{ site.url }}/{{ site.baseurl }}/images/GridPlot.png){:width ="75%"}

Note that the indexing starts from 0. The maximum values of column and row are calculated automatically based on the maximum possible requirement to place all the elements. Also, please note that, if `rowspan` and `colspan` are not defined, they will be assumed to be 1.

The placement for Widgetbox can be updated in the **Options** block. The placement parameters for the plots can be updated in the configuration dialog box in the plot.

----------------
This concludes the tutorial for `gr-bokehgui` module. All primary features of the module are explained here.

<!--The following screencast covers the tutorial.<br>-->
<!--<iframe width="560" height="315" src="https://www.youtube.com/embed/0LNlwYrcjps" frameborder="0" allowfullscreen></iframe><br>
-->

For suggestions/queries/comments on the module and the tutorial, kindly drop a mail to [`discuss-gnuradio`][discussion_forum].



[discussion_forum]: mailto:discuss-gnuradio@gnu.org
[guided_tutorial]: https://wiki.gnuradio.org/index.php/Guided_Tutorial_GRC
[codebase]: https://github.com/kartikp1995/gr-bokehgui.git
[link]: http://localhost:5006/bokehgui?bokeh-session-id=tutorial

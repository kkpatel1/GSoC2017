---
layout: post
title:  "Week 7: The evaluation week"
date:   2017-06-30 00:00:00 +0530
---

This week, I added a Base Sink template class. It will be common class for all sinks. Following are the updates of the week:

### Current Status
#### Added a base sink
The motivation of this concept was to remove the redundancy of code between all various sinks. The task of base class will be to manage the data-buffer operations which are almost common in all sinks. Some of the examples are:
1. `work` function of the sink - stores input stream in a buffer
2. `get_plot_data` function of the sinks - create an array of values to be sent to Python

Following is proposed structure of base sink template class. The implementation of base-sink is available on [`base_sink_impl`][base_sink_impl] branch.<br>
![BaseSink Structure]({{ site.url }}/{{site.baseurl}}/images/base_sink_struct.png){:width="75%"}

The base class contains the complete implementations of the functions like `work`, `get_plot_data`, `handle_pdus`, constructor initializations related to data-buffers. The base class template also contains definition of virtual functions which are specific to the sink and are called from the functions defined in base class. Example of such functions are `process_plot_data` and `work_other_buffers` for processing the data just before sending to Python via `get_plot_data` and processing the buffers other than data (like tag buffers) in `work` function respectively.

The template class parameters `class T` and `class U` defines the type of values the sink will be working with. In a sink, the input data stream is of type T, and _output_ data array (in function `get_plot_data`) is of type U.

In this structure, the base sink class is inherited as a virtual class instead of the `sync_block` class in standard GNU Radio block. The reason for change is: sequence of the constructors called when initializing object. The virtual inheritance slightly disturbs the _natural_ flow of constructor calls. Although there is a change in standard block structure, the overall idea is still same as standard block.

As of now, the current struture can not integrate the `AUTO` and `NORM` triggers because of different styles of trigger checks in different sinks. I am trying find a good _structured_ way of implementation. Feedback from the community would be grateful.

*As of now, the base sink is integrated in `time_sink_f` sink only. The remaining 3 sinks implemented till now will be integrated by starting of next week.*
#### Feedback required
To make these bokeh based GUI a _bug-less_ software, we would like to have feedbacks from the community. You can now test using GRC.

As of now, the working implementations of sinks are on [`develop`][develop_branch] branch.

To follow implementation and integration of base sink class, follow [`base_sink_impl`][base_sink_impl] branch.

For any comments/feedbacks/suggestions, you can drop an email to [`discuss-gnuradio`][discussion_forum].

-------------------------
### To-Do list for next week:
1. Solve the bugs of TimeSink and FreqSink:<br>
I don't believe my code is perfect. Kindly reinforce my belief! Add as much bugs as possible. It is now easier with GRC integration!
2. Integration of base sink template class to remaining 3 sinks
3. Implementing `textbox` and `label` widgets

[previous_post]: /GSoC2017/2017/06/16/TimeSink4.html
[develop_branch]: https://github.com/kartikp1995/gr-bokehgui/tree/develop/
[base_sink_impl]: https://github.com/kartikp1995/gr-bokehgui/tree/base_sink_impl/
[discussion_forum]: mailto:discuss-gnuradio@gnu.org

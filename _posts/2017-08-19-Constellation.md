---
layout: post
title:  "Week 14: Constellation week"
date:   2017-08-19 00:00:00 -0600
---

Following are the updates of the week:

### Current Status
#### Waterfall sink
The Waterfall sink for complex values was implmented this week. I added GRC integration for both float as well as complex waterfall sinks. I have also added customizations like multiple color pallettes in both sinks. The screenshots display typical display of watefall sinks.

![Screenshot_Waterfall]({{ site.url }}/{{site.baseurl}}/images/Waterfall_Screenshot.jpeg){:width="75%"}

#### Constellation sink
This week, the implementation of Constellation sink for complex values was completed. GRC integration for the same was added. Since, the time sink and constellation sinks are basically different ways of displaying same data, both have exactly same procedure for data collection and data storage. Hence, the C++ side of the sink is exactly same as the C++ implementation of time sink. Hence, instead of re-writing that, constellation sink directly uses the class `time_sink_c_proc` for the task. The following screenshots shows the typical display of the constellation sink.

![Screenshot_Constellation]({{ site.url }}/{{site.baseurl}}/images/Const_Screenshot.jpeg){:width="75%"}

### To-Do list for next week
There are mainly 5 tasks for next week
1. Do some cleanups and push the required changes in core GRC code to the main GNU Radio repository.
2. Write in-code documentations. Epescially in the functions which are not obvious to follow. Add a detailed README for the project.
3. Cleanup the code. Try to update the code with PEP8 guidelines. Cleanup not-so-important variables, reduce the redundancy, change the code structure.
4. Write a tutorial. I will mostly follow QT GUI tutorial. But will focus on what is different from QT equivalent.
5. Change the orientation of waterfall plot such that Frequency is on the horizontal axis. I will change the coffeescript implementation of the plot for this. Hence, there will be no changes in API of the project.

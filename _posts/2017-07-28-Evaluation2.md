---
layout: post
title:  "Week 11: Another evaluation week"
date:   2017-07-28 00:00:00 +0530
---

This week I tried to develop a prototype for waterfall sink. Following are the updates of the week:

### Current Status
#### Branch merging
Now, [`master`][master_branch] branch contains stable version of code with all widgets and two sinks (time and frequency sinks). Next developments of remaining sinks will be done on [`develop`][develop_branch] branch.

#### Implemented Checkbox and Radio buttons
The Checkbox and radio button widgets were implemented. Using a drop down instead of the radio button is not available. Since, it was not on timeline, I will implement it once I find some time later.

#### Waterfall sink
I am trying to implement waterfall sink based on an [example][exampleDemo] of Bokeh. Though it is a horizontal spectrogram, and GNU Radio users have good experience in vertical spectrogram, I am trying to developing similar spectrogram. This requires whole new type of plot that Bokeh doesn't directly provides. Hence, I am learning basics of the coffeescript and how to implement the plot. I have developed major part of the Bokeh side implementation but minute issues are taking too much time. Hopefully, I will be done by this weekend. So, by the mid of next week, I will try to complete whole implementation of waterfall sink. 

#### Feedback required
Since, the module has a substantial features, you can start using it. For any queries/feedback, drop me a mail and keep [`discuss-gnuradio@gnu.org`][discussion_forum] in CC.

-------------------------
### To-Do list for next week:
1. Complete Waterfall sink
2. Start work on Historgram sink

[develop_branch]: https://github.com/kartikp1995/gr-bokehgui/tree/develop/
[master_branch]: https://github.com/kartikp1995/gr-bokehgui/tree/master/
[discussion_forum]: mailto:discuss-gnuradio@gnu.org
[exampleDemo]: https://www.youtube.com/watch?v=L6p7Cd3uDis

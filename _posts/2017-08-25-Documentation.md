---
layout: post
title:  "Week 15: Documentation week"
date:   2017-08-25 00:00:00 -0600
---

Following are the updates of the week:

### Core GRC changes:
I did some clean up and added a pull request to core GNU Radio repository. You can review the PR [here][PR]. This contains all modifications required in core GRC code in GNU Radio.

### Code cleanup
Cleaned up code in C++ as well as Python side implementations. Added in-code documentation wherever required. Updated Python code to follow PEP8 guidelines. Code cleanup includes removing redundant variables and redundant imports in Python and C++ and splitting long lines.

### Tutorial
Added a thorough tutorial at [`/GSoC2017/tutorial/`][tutorial]. It also contains a screencast demonstrating the tutorial on video.

The following screencast covers the tutorial.<br>
<iframe width="560" height="315" src="https://www.youtube.com/embed/EyNOE9icNVc" frameborder="0" allowfullscreen></iframe><br>

-----------
### To-Do list for next weekend
1. GRC files cleanup: Define default values on some parameters. Also, add documentation and detailed `<check>` tags to avoid incorrect inputs from users.
2. Add a README file. It will list swoftware requirements, setup guide, some screenshots, list of features that remain to be implemented, and other notes.
3. I will try to change the Waterfall plot orientation so that the plot flows from top-to-bottom. Still struggling with it.


[PR]: https://github.com/gnuradio/gnuradio/pull/1434
[tutorial]: /GSoC2017/tutorial/

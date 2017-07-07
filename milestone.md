---
layout: page
title: Milestones
permalink: /milestones/
---

After discussion with mentor, we will be following a timeline as described below. We have changed the sequence of the features to be implemented based on the usage and necessity.


[**8th May - 14th May: Introduction**][week0]
 1. Introducing to the community
 2. Finalized weekly update procedure
 3. Finalized repository structure

[**15th May - 21st May: Planning**][week1]
 1. Refining the timeline and defining milestones of the project
 2. Finalize mechanism of starting the bokeh server and application
 3. Finalize the structure and dataflow of the module
 4. Understanding the Bokeh Library
 
---------------------------
### Phase 1 : Time sink and Frequency sink
[**22nd May - 28th May: TimeSink: Coding week 1**][week2]:
 1. Setup the structure
 2. Work on _time\_sink\_f.py_
 3. Work on _time\_sink\_f\_impl.cc_ and conclude _time\_sink\_f.py_

[**29th May - 4th June: TimeSink: Coding week 2**][week3]:
 1. Tag display support
 2. Performace evaluation

[**5th June - 11th June: TimeSink: Coding week 3**][week4]:
 1. Define generation of _top\_block.py_. Change _main_ function if using _gr-bokehgui_.
 2. Complete TimeSink
 3. Add GRC block

[**12th June - 18th June: TimeSink: Coding week 4**][week5]:
 1. Start Frequency Sink

[**19th June - 25th June: Frequency Sink: Coding week 1**][week6]:
 1. Complete Frequency Sink
 2. Add GRC block of Frequency Sink
 3. Add GRC example with multiple sinks (at different rates)

**26th June - 30th June: Evaluation 1: Time sink and Frequency sink**

-------------------------
### Phase 2 : Input widgets and Layout
[**26th June - 2nd July: Evaluation week 1**][week7]:
 1. Start working on Textbox and Labels

[**3rd July - 9th July: Widgets 1**][week8]:
 1. Complete work on Textbox and Labels

**10th July - 16th July**:
 1. Complete work on Slider and RangeSlider
 2. Setup Layout

**17th July - 23rd July**:
 1. Complete working on Layouts
 2. GRC examples with new inputs + multiple sinks in a different layouts
 3. Start working on Waterfall sink (develop a prototype)

**24th July - 28th July: Evaluation 2: Input widgets and Layout with Waterfall sink prototype**

-------------------------
### Phase 3 : Waterfall sink, Histogram sink, Constellation sink and BER sink
**24th July - 30th July**:
 1. Complete Waterfall sink

**31st July - 6th August**:
 1. Work on histogram sink

**7th August - 13th August**:
 1. Complete histogram sink
 2. Start working on Constellation display

**14th August - 20th August**:
 1. Complete constellation display
 2. Complete BER display

**21st August - 29th August: Final Evaluation: Waterfall, Histrogram, Constellation and BER sink**
 1. Conclude previous works
 2. Submit final evaluation


[week0]: /GSoC2017/2017/05/12/introduction.html
[week1]: /GSoC2017/2017/05/19/planning.html
[week2]: /GSoC2017/2017/05/26/TimeSink1.html
[week3]: /GSoC2017/2017/06/02/TimeSink2.html
[week4]: /GSoC2017/2017/06/09/TimeSink3.html
[week5]: /GSoC2017/2017/06/16/TimeSink4.html
[week6]: /GSoC2017/2017/06/23/FreqSink1.html
[week7]: /GSoC2017/2017/06/30/Evaluation1.html
[week8]: /GSoC2017/2017/07/07/Widgets1.html

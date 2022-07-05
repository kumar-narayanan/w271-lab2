Statistical Methods for Discrete Response, Time Series, and Panel Data
(W271): Lab 2
================

# The Keeling Curve

In the 1950s, the geochemist Charles David Keeling observed a seasonal
pattern in the amount of carbon dioxide present in air samples collected
over the course of several years. He was able to attribute this pattern
to the variation in global rates of photosynthesis throughout the year,
caused by the difference in land area and vegetation cover between the
Earth’s northern and southern hemispheres.

In 1958 Keeling began continuous monitoring of atmospheric carbon
dioxide concentrations from the Mauna Loa Observatory in Hawaii and soon
observed a trend increase carbon dioxide levels in addition to the
seasonal cycle. He was able to attribute this trend increase to growth
in global rates of fossil fuel combustion. This trend has continued to
the present, and is known as the “Keeling Curve.”

    ## Warning: package 'tsibble' was built under R version 4.1.3

    ## Warning: package 'latex2exp' was built under R version 4.1.3

![](lab_prompt_files/figure-gfm/plot%20the%20keeling%20curve-1.png)<!-- -->

# Your Assignment

Your goal in this assignment is to produce a comprehensive analysis of
the Mona Loa CO2 data that you will be read by an interested,
supervising data scientist. Rather than this being a final report, you
might think of this as being a contribution to your laboratory. You and
your group have been initially charged with the task of investigating
the trends of global CO2, and told that if you find “anything
interesting” that the team may invest more resources into assessing the
question.

Because this is the scenario that you are responding to:

1.  Your writing needs to be clear, well-reasoned, and concise. Your
    peers will be reading this, and you have a reputation to maintain.
2.  Decisions that you make for your analysis need also be clear and
    well-reasoned. While the main narrative of your deliverable might
    only present the modeling choices that you determine are the most
    appropriate, there might exist supporting materials that examine
    what the consequences of other choices would be. As a concrete
    example, if you determine that a series is an AR(1) process your
    main analysis might provide the results of the critical test that
    led you to that determination and the results of the rest of the
    analysis under AR(1) modeling choices. However, in an appendix or
    separate document that is linked in your main report, you might show
    what a MA model would have meant for your results instead.
3.  Your code and repository are a part of the deliverable. If you were
    to make a clear argument that this is a question worth pursuing, but
    then when the team turned to continue the work they found a
    repository that was a jumble of coding idioms, version-ed or
    outdated files, and skeletons it would be a disappointment.

# Report from the Point of View of 1997

For the first part of this task, suspend reality for a short period of
time and conduct your analysis from the point of view of a data
scientist doing their work in the early months of 1998. Do this by using
data that is included in *every* R implementation, the `co2` dataset.
This dataset is lazily loaded with every R instance, and is stored in an
object called `co2`.

## (3 points) Task 0a: Introduction

Introduce the question to your audience. Suppose that they *could* be
interested in the question, but they don’t have a deep background in the
area. What is the question that you are addressing, why is it worth
addressing, and what are you going to find at the completion of your
analysis. Here are a few resource that you might use to start this
motivation.

-   [Wikipedia](https://en.wikipedia.org/wiki/Keeling_Curve)
-   [First Publication](./background/keeling_tellus_1960.pdf)
-   [Autobiography of Keeling](./background/keeling_annual_review.pdf)

## (3 points) Task 1a: CO2 data

Conduct a comprehensive Exploratory Data Analysis on the `co2` series.
This should include (without being limited to) a [description of how,
where and why](https://gml.noaa.gov/ccgg/about/co2_measurements.html)
the data is generated, a thorough investigation of the trend, seasonal
and irregular elements. Trends both in levels and growth rates should be
discussed (consider expressing longer-run growth rates as annualized
averages).

What you report in the deliverable should not be your own process of
discovery, but rather a guided discussion that you have constructed so
that your audience can come to an understanding as succinctly and
successfully as possible. This means that figures should be thoughtfully
constructed and what you learn from them should be discussed in text; to
the extent that there is *any* raw output from your analysis, you should
intend for people to read and interpret it, and you should write your
own interpretation as well.

## (3 points) Task 2a: Linear time trend model

Fit a linear time trend model to the `co2` series, and examine the
characteristics of the residuals. Compare this to a quadratic time trend
model. Discuss whether a logarithmic transformation of the data would be
appropriate. Fit a polynomial time trend model that incorporates
seasonal dummy variables, and use this model to generate forecasts to
the year 2020.

## (3 points) Task 3a: ARIMA times series model

Following all appropriate steps, choose an ARIMA model to fit to the
series. Discuss the characteristics of your model and how you selected
between alternative ARIMA specifications. Use your model (or models) to
generate forecasts to the year 2022.

## (3 points) Task 4a: Forecast atmospheric CO2 growth

Generate predictions for when atmospheric CO2 is expected to be at [420
ppm](https://research.noaa.gov/article/ArtMID/587/ArticleID/2764/Coronavirus-response-barely-slows-rising-carbon-dioxide)
and 500 ppm levels for the first and final times (consider prediction
intervals as well as point estimates in your answer). Generate a
prediction for atmospheric CO2 levels in the year 2100. How confident
are you that these will be accurate predictions?

# Report from the Point of View of the Present

One of the very interesting features of Keeling and colleagues’ research
is that they were able to evaluate, and re-evaluate the data as new
series of measurements were released. This permitted the evaluation of
previous models’ performance and a much more difficult question: If
their models’ predictions were “off” was this the result of a failure of
the model, or a change in the system?

## (1 point) Task 0b: Introduction

In this introduction, you can assume that your reader will have **just**
read your 1997 report. In this introduction, **very** briefly pose the
question that you are evaluating, and describe what (if anything) has
changed in the data generating process between 1997 and the present.

## (3 points) Task 1b: Create a modern data pipeline for Mona Loa CO2 data.

The most current data is provided by the United States’ National Oceanic
and Atmospheric Administration, on a data page
\[[here](https://gml.noaa.gov/ccgg/trends/data.html)\]. Gather the most
recent weekly data from this page. (A group that is interested in even
more data management might choose to work with the [hourly
data](https://gml.noaa.gov/aftp/data/trace_gases/co2/in-situ/surface/mlo/co2_mlo_surface-insitu_1_ccgg_HourlyData.txt).)

Create a data pipeline that starts by reading from the appropriate URL,
and ends by saving an object called `co2_present` that is a suitable
time series object.

Conduct the same EDA on this data. Describe how the Keeling Curve
evolved from 1997 to the present, noting where the series seems to be
following similar trends to the series that you “evaluated in 1997” and
where the series seems to be following different trends. This EDA can
use the same, or very similar tools and views as you provided in your
1997 report.

## (1 point) Task 2b: Compare linear model forecasts against realized CO2

Descriptively compare realized atmospheric CO2 levels to those predicted
by your forecast from a linear time model in 1997 (i.e. “Task 2a”). (You
do not need to run any formal tests for this task.)

## (1 point) Task 3b: Compare ARIMA models forecasts against realized CO2

Descriptively compare realized atmospheric CO2 levels to those predicted
by your forecast from the ARIMA model that you fitted in 1997
(i.e. “Task 3a”). Describe how the Keeling Curve evolved from 1997 to
the present.

## (3 points) Task 4b: Evaluate the performance of 1997 linear and ARIMA models

In 1997 you made predictions about the first time that CO2 would cross
420 ppm. How close were your models to the truth?

After reflecting on your performance on this threshold-prediction task,
continue to use the weekly data to generate a month-average series from
1997 to the present, and compare the overall forecasting performance of
your models from Parts 2a and 3b over the entire period. (You should
conduct formal tests for this task.)

## (4 points) Task 5b: Train best models on present data

Seasonally adjust the weekly NOAA data, and split both
seasonally-adjusted (SA) and non-seasonally-adjusted (NSA) series into
training and test sets, using the last two years of observations as the
test sets. For both SA and NSA series, fit ARIMA models using all
appropriate steps. Measure and discuss how your models perform in-sample
and (psuedo-) out-of-sample, comparing candidate models and explaining
your choice. In addition, fit a polynomial time-trend model to the
seasonally-adjusted series and compare its performance to that of your
ARIMA model.

## (3 points) Task Part 6b: How bad could it get?

With the non-seasonally adjusted data series, generate predictions for
when atmospheric CO2 is expected to be at 420 ppm and 500 ppm levels for
the first and final times (consider prediction intervals as well as
point estimates in your answer). Generate a prediction for atmospheric
CO2 levels in the year 2122. How confident are you that these will be
accurate predictions?

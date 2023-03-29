+++
title = "Traffic violations in Bishkek"
author = ["Aidin Biibosunov"]
date = 2023-03-29T16:27:00+02:00
lastmod = 2023-03-29T16:28:28+02:00
tags = ["data-analysis"]
categories = ["blog"]
draft = false
type = "posts"
+++

<div class="ox-hugo-toc toc">
<div></div>

<div class="heading">Table of Contents</div>

- [**A bit about the data set**](#a-bit-about-the-data-set)
- [**Some basic questions**](#some-basic-questions)
    - [What is the most frequent traffic violation?](#what-is-the-most-frequent-traffic-violation)
    - [What about the cars?](#what-about-the-cars)
    - [Locations](#locations)
    - [Every day in a year](#every-day-in-a-year)
    - [Every hour in a day](#every-hour-in-a-day)
- [**Reproducibility**](#reproducibility)

</div>
<!--endtoc-->

Bishkek is the capital of Kyrgyzstan and, like many other cities around the world, it faces challenges related to traffic violations. Traffic violations can have a significant impact on road safety, traffic flow, and the environment. <br />
Traffic violation data analysis can help to evaluate the effectiveness of existing traffic safety interventions. So, in this blog post, I will analyze the data to better understand the situation.


## **A bit about the data set** {#a-bit-about-the-data-set}

I gathered the data from the [Open Data Platform of Kyrgyzstan](https://data.gov.kg/en/). The data set is constucted from [these](https://data.gov.kg/dataset/peectp-hapywehnn-npoekta-be3onachbin-ropod) excel sheets. The available[^fn:1] period is from 01.09.2019 - 30.04.2021. The provided information:

-   `id` - unique identification number of the violation
-   `car_brand` - vehicle brand
-   `car_model` - vehicle model
-   `violation_date` - the date of the violation
-   `crossroad_name` - the location (street) of the violation
-   `violation_protocol_name` - violation name
-   `violation_ammount`[^fn:2] - violation amount (fine in KGS)

I do not know how the data was collected. Hence, I cannot guarantee that it is reliable. So, treat the findings with a grain of salt. <br />
Of course it would be great if we had more information such as: gender, age, etc.


## **Some basic questions**[^fn:3] {#some-basic-questions}


### What is the most frequent traffic violation? {#what-is-the-most-frequent-traffic-violation}

To answer this question we can make a horizontal bar plot.

![](/images/traffic_violation_files/violation_counts.png "")

[ _To enlarge the images click on the them! ]_

We see that "_Exceeding the speed limit by more than 10 km/h, but not more than 20 km/h_" dominates with almost 50% of all the cases. Moreover, the fine for this violation type consist of 1000 KGS. <br />
It would be interesting also to have crash reports -  reports which include information on traffic accidents, including the causes of the accident, the vehicles involved, and any injuries or fatalities.

Thus, we expect that the most frequent fine is 1000 KGS. Which is confirmed in the figure below.

![](/images/traffic_violation_files/fine_counts.png "")

The collected fine is distributed as follows [[source](https://ru.sputnik.kg/20211007/bezopasnyj-gorod-dengi-raspredelenie-skhema-1054145313.html)]: _"Vega" company receives about 215-216 KGS from each violation, then 2.6 million KGS for technical support of the "Safe City" system, on which operators of the Monitoring Center process data._

The distribution of the rest of the funds:

-   5% to the State Committee of National Security for the maintenance and servicing of the backup data processing center;
-   About 25% to the mayor's office, local authorities for the creation of road infrastructure, installation of markings, signs and other things;
-   5% cent to the Ministry of Transport and Roads for the creation of road infrastructure conditions
-   About 15% to the Main Directorate for Road Safety for creating conditions for patrol cars, the operation of the Monitoring Center, payment for the work of its operators.

Besides, I am not sure if all of the cases were confirmed by an operator.


### What about the cars? {#what-about-the-cars}

First, let's look at the car brands.

![](/images/traffic_violation_files/top20_car_brands.png "")

The top-3 cars are: Toyota, Honda and Mercedes-Benz respectively.
Is it just because these brands are the most common in Bishkek? <br />
[Here](https://ru.sputnik.kg/20211126/kyrgyzstan-avtomobil-top-rejting-1054743470.html) it was reported[^fn:4] that the top-5 cars in Kyrgyzstan by number are:

1.  Mercedes-Benz (141 618)
2.  Daewoo (139 406)
3.  AvtoVAZ (137 485)
4.  Toyota (128 672)
5.  Honda (118 722)

So, at least they are among the five most popular cars. But it is better to confirm it by youself.

Second, more in detail - including the car models:

![](/images/traffic_violation_files/top20_cars.png "")

We have two leaders: _Honda Fit_ and _Toyota Camry_.


### Locations {#locations}

Now, it is interesting to look at the locations that have the highest incidence of traffic violations.

![](/images/traffic_violation_files/top20_crossroads.png "")

There is a clear leader: _Zhibek-Zholu 291_

Let's look more closely on top-5 crossroads by projecting them on the map. Along with the top-5 car models for each of the selected crossroads.

<iframe src="/images/traffic_violation_files/street_interactive_map.html" width="100%" height="500"></iframe>

Ideally, traffic violation data analysis can help to identify high-risk areas where accidents are more likely to occur due to traffic violations. By understanding where and why violations are occurring, authorities can take steps to improve safety in these areas.


### Every day in a year {#every-day-in-a-year}

For this I plotted heatmaps in a calendar format.

![](/images/traffic_violation_files/heatmap_by_year_2019.png "")

We observe that cold months have less incidents than warm ones. There is a clear deacrease/increase in number of violations as we approach winter/summer.

![](/images/traffic_violation_files/heatmap_by_year_2020.png "")

The data for the year 2020 shows an unusual trend in the months of March and July, with a high number of violations in March and a low number in July. This leads to the question of whether this could be related to the COVID-19 lockdown measures.

![](/images/traffic_violation_files/heatmap_by_year_2021.png "")


### Every hour in a day {#every-hour-in-a-day}

Here I plotted number of traffic violations in 24 hours. For all the years aggregated and separately for each year.

![](/images/traffic_violation_files/viol_24h_combined.png "")

The highest numbers are around 14-15 hours. Interestingly, the pattern remains consistent across all the years.

By monitoring changes in traffic violation rates over time, authorities can determine whether interventions such as education campaigns or enforcement initiatives are having a positive impact.


## **Reproducibility** {#reproducibility}

The code with the analysis is in this [repo](https://github.com/aidinbii/traffic%5Fviolation%5FKG/tree/master). You can generate all the tables and figures presented in this post yourself.

Please feel free to comment. And if you have any questions, contact me.

[^fn:1]: I excluded sheets from 03.2019 - 08.2019 because of the different formatting and table structure
[^fn:2]: The typo is done by the creator of the sheets
[^fn:3]: The results are aggregated for the whole period except when stated otherwise
[^fn:4]: As of 15.12.2021
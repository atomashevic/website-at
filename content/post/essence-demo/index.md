---
title: 'Demonstration page for ESSENCE project'
subtitle: 'Demo page containing code, output and embedded Shiny app'
summary: This page demonstrates some of the features which will be contained in open access reproducible code which will be part of ESSENCE project website.
authors:
- admin
featured: false
draft: true


# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []

---

{{% alert note %}}
This page was created for demonstration purposes and is a part of ESSENCE project grant application for PROMIS call of Science fund of Republic of Serbia.
{{% /alert %}}

This page demonstrates how reproducible R code can be presented to wide audience. Specifically, it is aimed at showing how ESS data can be easily imported into R and how different types of analysis can be performed. 

Visitors and users of open code platforms (such as one envisioned by ESSENCE project) can copy code stored in the repository, reproduce the analysis and compare the output. The basic idea of ESSENCE project (RA section) is to aggregate open code and let users reproduce the analysis and then contribute to the repository with their own code.

Simultaneous publishing and sharing of both code, results and commentary/interpretation is crucial for reproducible analysis as part of open science framework in order to improve scientific research and increase transparency of scientific analysis.

## Loading ESS data in R using *essurvey* package

*essurvey* package is a simple R package which enables ESS data users to quickly import desired ESS data in R without a need to download any specific files or convert files from file formats foreign to R.

```r
install.packages("essurvey")
library("essurvey")
```

This package communicates directly with the ESS database. As with regular use of ESS data in order to access it, the user has to [register on ESS website](https://www.europeansocialsurvey.org/user/new) in order to access the data. After registration, using registered e-mail the user can access the data. Same applies for using *essurvey* package. In order to authenticate, user has to enter their e-mail into R.

```r
# replace user_email with your registered email, e.g. petarpetrovic@gmail.com
set_email("user_email")
```

This package enables users to access data by country or to access the entire data for a specific round of ESS.

In this example, we show how to access data for one country, for specific round of ESS, namely the data for Slovenia for round 8.

```r
data <- import_country("Slovenia", 8)
```

ESS raw data includes codes for missing values stored inside the variables. At this point, R will read these values as non-missing. Following code, based on a procedure from the *essurvey* package fixes issues with those variable codes.

```r
data <- recode_missings(data)
```

Using *RStudio* or any other R GUI, it's possible to explore the variable list of *data* object which now contains properly coded round 8 data for Slovenia.

hhmmb

eisced

<iframe src="https://atomasevic.shinyapps.io/essence-shiny/" style="border:none;width:1000px;height:800px;"></iframe>
---
title: "Getting Started with R, R Studio, and Slack"
author: "Gov 50"
date: 2025-09-02
summary: >-
  A guide to installing and setting up the software required for
  Gov 50. 
output: pdf_document
---

## Installing R and RStudio

In this problem set, we're going to get R, RStudio, and R Markdown set up on your computer. To get started, follow these steps: 

1. Download and install the most recent version of [R (click me)][]. There are versions available for the Windows, Mac, and Linux operating systems. On a Windows machine, you will want to install using the `R-x.y.z-win.exe` file where `x.y.z` is a version number. On a Mac, you will want to install using the `R-x.y.z.pkg` file that is notarized and signed. 

2. With R installed, download and install [RStudio (click me)][]. RStudio is a type of "integrated development environment" or IDE designed for R. It makes working with R considerably easier and is available for most platforms. It is also free. 

3. Open the .Rmd version of this file in RStudio. Install the packages we will use throughout the semester. To do this, either type or copy and paste each of the following lines of code into the "Console" in RStudio (lower left panel by default). Make sure you do this separately for each line. If you are asked if you want to install any packages from source, type "no". Note that the symbols next to `my_package` are a less than sign `<` followed by a minus sign `-` with no space between them. (Don't be worried if you see some red text here. Those are usually just messages telling you information about the packages you are installing. Unless you see the word `Error` you should be fine.)

```{r, eval = FALSE}
my_packages <- c("tidyverse", "usethis", "devtools", "learnr",
                 "gitcreds")
install.packages(my_packages, repos = "http://cran.rstudio.com")
```

4. For some things in the course, we'll need produce PDFs from R and that requires something called LaTeX. If you've never heard of that, it's completely fine and you should just run the following two lines of R code:

```{r, eval = FALSE}
install.packages('tinytex')
tinytex::install_tinytex()  # install TinyTeX
```

## Joining the Course Slack

5. In the left hand menu on Canvas click the item called Slack. Slack is the main way forum we will use to send out announcements and answer questions for this course. Post a short introduction message in the \#general channel (e.g. `Hi all, my name is Noah and I'm looking forward to this class`) 

## Submitting

6. Click the `Knit` button near the top of the RStudio window, this should create a pdf version of this document in the same place you are storing this .Rmd file (we strongly recommend having a dedicated folder for Gov50 assignments). If you encounter any issues knitting seek help from a TF or CA. Upload the pdf in Gradescope (can be reached via the left hand menu on Canvas) under the assignment `Problem Set 0: Getting Started`. This along with your written introduction in Slack constitutes the assignment. This assignment is graded on completion only.


[R (click me)]: https://cloud.r-project.org/
[RStudio (click me)]:https://posit.co/download/rstudio-desktop/

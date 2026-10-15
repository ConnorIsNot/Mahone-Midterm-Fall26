# GES 778 midterm project

**Due Friday, Oct 30, 11:59pm**

## Intro

For your midterm, you will use one or more datasets, either that I've provided
in the `justviz` package, or that you bring in yourself, to complete a short
data visualization project. Only bring your own data if it serves your academic
and professional goals; it will be more work and won't get you extra credit.

Your project should be a cohesive document, so all the charts and the table tell
a story together. You decide what you want to do and how, and you decide who
your hypothetical audience is, then work with that audience in mind.

If done well, this project should be something you can send as part of a job or
fellowship application.

This repo is a scaffold for your project. To get you started, it contains the
following files:

```
.
├── code
│   ├── 01_eda.qmd
│   ├── 02_sketches.qmd
│   └── 03_final_draft.qmd
├── data
├── docs
│   ├── abstract.md
│   └── technical_notes.md
├── midterm.Rproj
├── plots
├── _quarto.yml
├── README.md
└── utils

```

## Requirements

You will hand in the following, all within this repo:

- An **EDA** Quarto notebook and its rendered markdown
- A **sketches** / rough draft Quarto notebook and its rendered markdown
- A **final draft** Quarto notebook and its rendered markdown with 3 charts and
  1 table, all related to each other
  - If you make a chart with a ggplot extension that we haven't used in class,
    that can count for 2 charts. See the list of acceptable extensions in
    `./extensions.md`.
- **Technical notes**. This is a short, informal markdown document (bulletpoints
  are great) laying out details of what you did, what technical decisions you
  made and why, and guidance on working with your code further. Focus on what's
  in the final draft notebook, but explain ways you manipulated data leading up
  to the final draft. Think of it as notes you'll reference when you use parts
  of your code at your next job or your capstone a year from now, or how you'll
  acquaint another developer with your code.
- **Abstract**. This is a short, non-technical markdown document giving a
  high-level overview of the project explaining your decisions to a non-coder,
  focused more on what you set out to do, how you revised it, and what lessons
  you incorporated from the readings and case study. It should also briefly
  state the sources of your data (don't need to use formal citations). If you
  were to send your project as a work sample for a job, this would be its intro.
  400 words max.

## Code

Some good coding practices you should use here:

- Separate concerns in separate places:
  - Utilities and snippets go in scripts in the `./utils` folder
  - EDA, sketches / rough drafts, and final versions go in different notebooks
  - If you have any additional data, it goes in the `./data` folder
  - When you export final copies of plots, they go in the `./plots` folder
- Use notebooks and knit / render them often
- Write comments & notes in your notebooks as you work, so your final write-up
  will be easier
- Make git commits often and push them to GitHub often, with informative commit
  messages (e.g. "Adjust colors in EDA charts" rather than "Work on charts")

You should not be using AI to generate your code or do analysis. Acceptable use
of AI for this project is limited to debugging code that you have written
yourself and are able to explain. You should note where you do this in your code
(e.g. comment "Debugged the arguments of this function with Claude").

All notebooks must have a rendered markdown version in the repo, and should be
able to run without error on another machine with little to no adjustment.

## Exploratory data analysis / visualization

Your first step is to **figure out what you're interested in visualizing**. Look
through the datasets in the justviz package and decide which one(s) you'd like
to work with (you are free to join datasets or do additional calculations if
you'd like), and which variables you'll use. Conduct EDA, focusing on your
chosen variables. Refer back to [chapter 10](https://r4ds.hadley.nz/eda) of *R
for Data Science* for an overview of what might go into EDA, and the [ggplot
documentation](https://ggplot2.tidyverse.org) for specific help. How you explore
a dataset depends on the data itself, but in general this notebook should
include:

- Distributions (boxplots, histograms, etc)
- Some descriptive statistics (start by calling `summary` on your data frame)
- Patterns between variables, if applicable (scatterplots)

Take notes as you go---what you're doing, why you're doing it, and especially
what you find in the process. By the time you're done, you should have a sense
of what story you want to tell.

## Sketches

In your sketches notebook, you'll take what you've decided you want to show, and
you'll work through different ways to approach it. You might want to choose some
of your EDA charts as a starting point, or do something new based on your
findings. This will involve **sketching on paper first**. Mark up your drawings
with some details to help you organize your thoughts (what goes on the axes,
what subsets of the data you might be using (e.g. each point in your scatterplot
is one tract, each bar in your bar chart is a county, etc)).

Then **sketch with code** to figure out what you'll want for your final charts.
Some examples of moving from EDA to a sketch are:

  | EDA                                                                 | Sketch                                                                                                             |
  | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
  | Scatterplot of 2 variables from the ACS dataset (x and y encodings) | Scatterplot of those same 2 variables, filtered for just metro areas and adding a 3rd variable via a size encoding |
  | Stacked bar chart                                                   | Separating those same bars with facets instead of stacking them                                                    |
  | Side-by-side (dodged) bar chart to show differences between groups  | Dot chart to show the same differences, but with better focus on the range of values in the dataset                |
  | Charts without clean, formatted labels and captions                 | Charts with formatted labels                                                                                       |

If you're doing any calculations or changing any variables and want to write
them out before moving on to your final visualizations, this is a good place to
do that.

By the end of this notebook, you will have decided on 2 to 3 charts that you'll
finalize, and you'll know what story you want to tell and how.

## Final draft

In your final draft, you'll have just a few chunks of code, 1 per chart. Your
project will be graded on each chart in this notebook, so keep your
experimentation in the EDA and sketches notebooks.

### Requirements for final draft charts

Every chart should be generated in its own code chunk, and each chunk should
have a unique label (`#| label: `). Each chart should have:

- A title and possibly a subtitle. Style (descriptive vs narrative) is up to
  you, depending on your intended audience.
- A caption giving the source of the data
- Clear definitions of what is being shown, for what locations and over what
  time periods
- Alt text written in the chunk's `#| fig-alt: ` option
- A copy saved to the `./plots` folder using `ggsave`, either a JPG or PNG file.
  File names should have your last name and a meaningful label (e.g.
  "seaberry-med-income-x-pm25-scatter.png")

Additionally, your table should be nicely formatted and printed using a function
that renders plain markdown (`knitr::kable` or other markdown-focused functions,
but not `gt`).

## Check-ins

You'll have multiple opportunities to check in about your project. The first
will be your very brief proposal and preliminary EDA, due 10/16. The second will
be a full-class work session on 10/20. We can also schedule an office hours
session between then and the 30th. If you're working steadily on this, there
won't be any surprises when it comes to grading; if you wait until the last
minute, you will have missed out on feedback.

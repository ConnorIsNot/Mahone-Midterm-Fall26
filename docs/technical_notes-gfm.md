# Technical notes
Connor Mahone
2026-11-04

This project is titled “Cuffing Season” and is focused on validating the
cuffing season trend using survey data while investigation seasonal
patterns in romantic relationships.

## Data

- Data was sourced from Stanford University How Couples Meet and Stay
  Together (HCMST) 2017 survey.

- This project uses the Rdata version 2.2 download.

- Fonts in the data folder are optional but were used in the charts

  - “Avenir Next Semi Condensed Demi” for titles

  - “Avenir Next Semi Condensed Regular” for everything else

## Code

- When beginning with EDA, I selected a few variables that I though may
  be of interest out of the over 700 variables provided. These variables
  focused on respondent age, important relationship milestone dates (met
  date, relationship start date, end date if applicable), as well as a
  variable about online dating and the analytic weight.

  - In my EDA I planned on how partner’s met so I pulled all relevant
    variables, but did not end up exploring them further.

- I created a subsetted dataset called cuffing_data with the relevant
  variables and certain new variables that I created.

  - w1_year_fraction_breakup was created to mimic the the year_fraction
    used for relationship start date

    - This was used to create the relationship_length variable

  - age_at_relstart was created using the respondents’ age and year of
    relationship start

- w1_ppage, w1_age_when_met, w1_age_at_relstart were all used to create
  custom age categories based on life stage

  - \< 20, 20-29, 30-49, 50+

  - These age groups were selected to ensure each group had a large
    enough sample size to be represented as a group, whereas the census
    groups had a lot of variation in sizes.

  - Respondents were adults when surveyed in 2017, however, some began
    relationships while they were minors. I initially overlooking this
    produced missing age categories. Adding the under 20 category
    accounted for those respondents while fitting them into a similar
    life stage.

- relstart_season, met_season, and breakup_season were created by
  grouping the responses to their respective months into their
  meteorological season.

  - Winter: Dec, Jan, Feb

  - Spring: Mar, Apr, May

  - Summer: Jun, Jul, Aug

  - Fall: Sep, Oct, Nov

- Because the survey over-sampled certain groups, such as LGBT
  individuals, the included w1_weight_combo variable was used so the
  data could more closely represent the population.

  - This was used in the geom_mosaic plot with the built-in weight
    argument

  - For plots/tables that didn’t have this function baked in, the
    dataset was converted to a srvyr object, after which dplyr’s grammar
    could be used to perform summary tasks on the data to prepare it for
    visualization.

- The charts were designed using ggplot’s framework and 2 different
  plugins

  - Chart 1: Seasonal relationship mosaic

    - Used ggmosaic

    - Applied a manually defined seasonal color palette

  - Chart 2: Monthly commitment visualization

    - Used ggdist’s geom_lineribbon

    - Displayed average time between meeting and relationship start by
      meeting month

    - Incorporated confidence intervals, calculated using the
      survey_mean function

  - Table 1: Relationship outcomes by season

    - Used knitr’s kable function to create a custom table

    - Summarized weighted instances and breakups

    - Calculated the ratio of breakups to instances

    - Values were small enough and featured little enough variation that
      a table was able to convey this

## Potential improvements / possible next steps

- This project uses retrospective survey responses from 2017, and the
  “cuffing season” trend has only grown (in usage of the phrase) since
  then.

- Because certain relationships started decades before the survey was
  performed, respondents may not remember exact dates.

- A more recent survey with categorized questions on medium of meeting
  would be interesting to see how the trend differs across different
  modes of contact.

  - This is possible using the survey data, but online dating has grown
    since then, and the survey asked about how partners met via an open
    ended question, making it more difficult to categorize.

- Because the survey was conducted over summer, it may ignore the
  (alleged) short-term nature of cuffing season, as some respondents may
  not report it as their most recent “real” relationship.

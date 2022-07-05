# Lab Instructions

- In this lab, you are going to apply what you have learned through the time series modeling section of the course onto a new dataset of $\text{CO}_2$ emissions. This will allow you to use each of the time series tools that you have developed in this section of the course to produce a complete analysis. 

## Submitting your lab 

You must submit a PDF of your compiled analysis and your code (.rmd) to Gradescope.

## Guidance

- In this report, you _should not_ need to show code that produces figures or tables; but, you _should_ show code that estimates models and standard errors. For example:
  - You should show code that estimates using `glm()` and `vcovHC`. 
  - But, you should now show code that produces `ggplot()` or `stargazer()` tables.
- You should use appropriate report writing style. 
  - Language should be professional. This does not mean "fancy" or "academic" but rather that it should show respect for the reader. The Dalal, Fowlkes and Hoadley (1989) paper that you read is a good model of this style of writing. 
- You should use an appropriate reporting style. 
  - Tables, figures, and models that you present are the evidence for the argument that you are making. 
  - Every part of your argument needs to be supported by evidence. 
  - You should not dilute the effectiveness of your evidence by including superfluous evidence. A good test for this is to evaluate whether every table and figure is discussed in the text, and also whether every argument you make in the text has a corresponding piece of evidence that you can point your reader to. 
  - Because you have only 10 pages, you will have to carefully consider what plots to show, and how to show them. 
- If you do any data wrangling, manipulation, filtering, or other similar task, this should **not** happen inside the report. This work should be conducted in a separate, modular file so that your report begins with the clean dataset that you would like to work with. 
- If you do any data wrangling, manipulation, filtering, or other similar task, this **should** be reproducible, so that there is a record for how you got from the raw data to the final data that you analyze. 
- If you have an `exploratory_data_analysis.Rmd` notebook in your repository, this should **not** be a file that is a "work in progress" notebook, or something that is just the team exploring. Instead, it should be purposeful, and descriptive so that a contributor to the project in the future can rapidly learn what you know about the data. There will very likely be _more_ in this notebook than you have space for in your report, but do not simply dump every view you make into this document. 
- Please, try to constrain yourselves to core libraries that we have presented at this point in the course. Suppose that those have already been cleared by the house statisticans at NASA. If you choose to use other libraries, or functions from other libraries, you should (a) justify their necessity; (b) build the package installs in a reproducible way, so that someone on an arbitrary computer can reproduce your work. This could involve a Docker container for your work; or, it could involve using `renv`. 

Students are expected to act with regard to UC Berkeley Academic Integrity.

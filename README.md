# REDCap Recruitment Tracker R Shiny Application - User Manual
## Biostatistics Core (BSC), Center for Clinical and Translational Science (CCTS)
## The University of Illinois at Chicago
## 08/08/2023

## <<Purpose>>
REDCap (Research Electronic Data Capture) is a nationwide online survey and database. To visualize any project involving
a randomized controlled trial (RCT) in REDCap, researchers can use the R Shiny application called “Recruitment Tracker.”
“Recruitment Tracker” aims to establish a free, interactive, and web-based dashboard
(https://uicccts.shinyapps.io/REDCap_Tracking/). The platform R Shiny allows users to interact with and visualize the data
according to their needs. The main function of this dashboard is to track the recruitment progress of an RCT project
using tools and functionalities that provide real-time statistical results. Thus, this dashboard can support users in making
decisions about recruitment progress and data collection based on the tracking reports.

The secondary function of the “Recruitment Tracker” is to visualize the characteristics of the participants assigned to
receive randomization in RCTs. Researchers can perform univariate and bivariate analyses on all demographic and clinical
variables of interest. All the results in the “Recruitment Tracker” presented in graphs and tables are able to be
downloaded.

The workflow of the modules of this interactive online dashboard is illustrated in Figure 1. “Recruitment Tracker” displays
the dataset in four modules of interest for users: “Verification & Setting,” “Project Summary,” “Recruitment Tracking,”
and “Descriptive Statistics.” “Recruitment Tracker” was made publicly available in Dec 2022. Advanced R Users may
request the R Shiny code to adapt the code for their specific visualization of R Shiny apps.

![fig1](https://github.com/souvik2019/ccts_rshiny/blob/main/images/fig1.png)
Figure 1. Workflow and modules of the interactive web-based dashboard for REDCap Recruitment Tracker Shiny App

## <<Module 1. Verification & Setting>>
This module is designed to import the user’s long-form longitudinal dataset involving RCT in REDCap (Figure 2
demonstrates the long-form format of an example dataset). Also, users must provide recruitment goals to compare with
recruitment progress. To do so, please follow the instructions as follows (See Figure 3):

**Step 1.** To import the dataset, users need to provide the token of the REDCap project of interest. Please note that it will
appear as asterisks to ensure data confidentiality as you enter the token.
Then, the real-time dataset can be pulled from the online REDCap database directly. This dashboard will not import or
analyze any variable involving personal information (i.e., identifier) to protect data privacy. Once the data are imported,
variables are automatically separated into categorical variables and numerical variables—based on the data dictionary
(codebook)—for the purpose of visualization and analyses.

**Step 2.** To produce the tracking statistics of the RCT project, users need to enter the following information into the boxes:
Research Period of this Clinical Trial Project, Total Targeted Number of Screened Participants, Expected Rate of Eligibility,
and Expected Rate of Randomization.

**Step 3.** To identify the RCT selection process variables in REDCap, users need to provide the five variable names assigned
to the information below. This app will present the recruitment progress based on the results of these five variables.

(1) The date that the participant received the screening process (follow the code rule: yyyy-mm-dd),
(2) Participant eligibility (following the code rule: 1= Yes and 0 = No),
(3) Exclusion reason for the RCT project (no cod rule),
(4) Whether the participant receives the randomization (following the code rule: 1 = Yes and 0 = No), and
(5) The date that the participant received the randomization (following the code rule: yyyy-mm-dd)

**Step 4 (Optional).** Users can upload the variable list in the "Variable List (Optional)" box to observe specific variables of
interest rather than all variables in the dataset. The content of the file should follow the rules below:

(1) All the variable names match those in REDCap, including both spelling and capitalization. Please note that the variable
list does not need to include the five variable names mentioned in Step 3,
(2) All the variable names are listed in column 1 of the file (See Figure 4),
(3) Rename “Sheet 1” on the Excel file to “variables,” and
(4) Please save the Excel file as a CSV file format.
Once the file is successfully uploaded, the message below the “Import” button will show “Uploaded file: filename.csv.”

**Step 5.** Once all the information is given, please press the green button labeled "Search." If the message below the
"Search" button shows "Dataset Successfully Imported," it indicates that the dataset was imported from the REDCap
database correctly, and the statistical results are ready to be revealed in the dashboard. However, the message will show
"Fail to find the REDCap Data" if users provide the wrong RCT project token in REDCap or the wrong data format rule of
the uploaded variable list. Then, users need to follow the above rules and go back to Step 1.

**Step 6. (Optional)** To save time for the future use of this dashboard, users can store all the setting information in Step 1
to Step 4. After the message "Dataset Successfully Imported" is shown on the window, please press the green button
labeled "Export" located below “Setting (Optional).” Then, all the setting information (including the optional variable list)
will be exported into a downloaded JSON file to the user's local desktop. Next time, when users want to use
"Recruitment Tracker," they can click the green button labeled "Import" and upload the JSON file. After doing this, users
can press the green bottom labeled "Search" and import the data directly.

![fig2](https://github.com/souvik2019/ccts_rshiny/blob/main/images/fig2.png)
Figure 2. An example of a long-form dataset

![fig3](https://github.com/souvik2019/ccts_rshiny/blob/main/images/fig3.png)
Figure 3. Import the REDCap dataset via project token and then provide the initial setting information

![fig4](https://github.com/souvik2019/ccts_rshiny/blob/main/images/fig4.png)
Figure 4. The data format of the optional variable list file (CSV file only)

## Example
This example demonstrates how to use this dashboard's module of "Verification & Setting." (See Figure 5). First, we
provide the token "A0C6E1AA3B6FF2F1EBF4A184FABE4378," of an artificial project we created in the REDCap database.
The research period of this project is from 2017-07-01 to 2020-06-30. The total targeted number of screened participants
is 2450, with an expected eligibility rate of 0.25 and an expected randomization rate of 0.90. In other words, in this RCT
project, the total expected number of the randomized participants is 551.25 (= 2450X0.25X0.90). We randomly assigned
the participants to receive either standard treatment or new treatment in this project.

The variable names for screening date, participant eligibility, the exclusion reason, randomization, and randomization
date are “screen_date,” "is_eligible," “exclusion_reason,” "is_enrolled," and "enrolled_date," respectively. Since we
prefer to analyze a specific variable list, we upload a CSV file named “variable.csv.”. Once we click the button of "Search,"
the message below "Search" should show "Dataset Successfully Imported." Then, we can further observe the statistical
results in the "Project Summary," "Recruitment Tracking," and "Descriptive Statistics” modules.

![fig5](https://github.com/souvik2019/ccts_rshiny/blob/main/images/fig5.png)
Figure 5. Import the REDCap example dataset via token and provide the initial setting information

## Module 2. Project Summary
After the data is successfully imported, this module provides the summary report of the RCT project. Figure 6 shows the
summary of the example dataset. The research period of this RCT project is from 2017-07-01 to 2020-06-30. The total
number of screened participants is 2450 in a total of 4 sites. Among the screened participants, 650 were eligible for the
RCT project. Among the eligible participants, there are 75 eligible participants excluded from the randomization step. The
exclusion reasons include “Not meeting the inclusion criteria”(38), “Declined to participate” (20), and “Other reasons”
(17).

Among the 575 participants (=650-75) who received randomization, 269 received the standard treatment while 306
received the new treatment. The randomization accrual rate is 104.31% (= actual 575/target 551.25). The average
number of randomized participants per site is 143.75 (=575/4). The mean number of days from screening to
randomization is 15.26, and the median is 15.

![fig6](https://github.com/souvik2019/ccts_rshiny/blob/main/images/fig6.png)
Figure 6. Project Summary of the example dataset
# Guide to Creating Your Own Report Templates
you can upload any docx file as a report template within ostrich birdseye. in order to get data dynamically into your report, you must use follow our spec for inserting tags into your template.
## Tag Structure
Our tags are structured as follows:

```
@example-tag@
```
there are static tags, which are strings that will be substituded with data, like the one above, and then there are dynamic tags which have elements that may change and fetch different data depending on the what is in the tag. Some examples of a dynamic tag as as follows:

```
@{insert question id here}-question-score@

#some examples:
@GV.OC-1-question-score@
@GV.OC-1-process-question-score@
@ID.AM-6-question-score@

```

Note: many of the assessment tags assume the following stucture of assessments:
```
{FUNCTION SHORT NAME}-{CATEGORY SHORT NAME}-{QUESTION NUMBER}-{ASPECT}
Examples:
GV-OC-1-process
ID-AM-6-process
```

## Ostrich Supported Tags
the following tags are supported by ostrich and will be replaced with data when the report is generated:
### Assessment Report Tags


```
@businessUnitName@
@date@
@currentUser@ (user that generated report)
@currentProfile@ (current profile for assessment)
@assessment@ (assessment name)
@subsNames@ (names of the practitioners for the assessment. In a rollup these are the business unit names)
@assessmentType@ (the content key for the assessment EG. NIST, MITRE, ect)
@{insert function name here}-function-image@ (get the chart for the function e.g. GOVERN, IDENTIFY, ect. Must be all caps)
@{insert function name here}-function-score@ (get the score for the function e.g. GOVERN, IDENTIFY, ect. Case Sensitive. Exlclude spaces)
@{insert question id here}-question-score@ (get the score for a question, category, function, or for the whole assessment (in that case use "summary"))
@{insert question id here}-target-score@ (get the target for a question, category, function, or for the whole assessment (in that case use "summary"))
@{insert question id here}-question-text@ (get the text associcated with a question, typically only used at the lowest level. e.g. GV.OC-1-process)
@{insert question id here}-target-text@ (get the text associcated with a target, typically only used at the lowest level. e.g. GV.OC-1-process)
@{insert question id here}-question-recommendation@ (get the recommendation associcated with a question, will only work at the lowest level. e.g. GV.OC-1-process)
@{insert question id here}-question-finding@ (get the finding associcated with a question, will only work at the lowest level. e.g. GV.OC-1-process)
@{insert question id here}-question-note@ (get the coverage associcated with a question, will only work at the lowest level. e.g. GV.OC-1-process)
@{insert question id here}-question-evidence@ (get the evidence associcated with a question, will only work at the lowest level. e.g. GV.OC-1-process)
@{insert question id here}-subs-scores@ (get a table with the sub name, score, and percet to target for a question, category, function, or for the whole assessment (in that case use "summary"))
@{insert question Id here}-subs-scores-no-header@ (get a table with no header row with the sub name, score, and percet to target for a question, category, function, or for the whole assessment (in that case use "summary"))
```

### CRQ Report Tags
```
@scenarioName@
@scenarioName2@ (if comparing two scenarios)
@date@
@generatedBy@
@currentUser@
@scenarioFamilyName@ (gets the name of the scenario family that the scenario is a part of)
@scenarioFamilyName2@ (if comparing two scenarios)
@scenarioFamilyDetails@ (gets the details of the scenario family that the scenario is a part of)
@scenarioFamilyDetails2@ (if comparing two scenarios)
@scenarioDetails@ (gets the details of the scenario)
@scenarioDetails2@ (if comparing two scenarios)
@selectedFactor@ (gets the selected factor for the scenario. Default is ALE)
@selectedFactor2@ (if comparing two factors)
@fairFactors@ (gets the factor data for the scenario)
@fairFactors2@ (if comparing two scenarios)
@aleChart@ (gets the ale chart for the simulation result)
@aleChart2@ (if comparing two scenarios)
@lossExceedanceChart@ (gets the loss exceedance chart for the simulation result)
@lossExceedanceChart2@ (if comparing two scenarios)
@whiskerChart@ (gets the whisker chart for the simulation result)
@whiskerChart2@ (if comparing two scenarios)
@histogramChart@ (gets the histogram chart for the simulation result)
@histogramChart2@ (if comparing two scenarios)
@riskPercentilesChart@ (gets the risk percentiles chart for the simulation result)
@riskPercentilesChart2@ (if comparing two scenarios)
@lossMagnitudeProportionChart@ (gets the loss magnitude proportion chart for the simulation result)
@lossMagnitudeProportionChart2@ (if comparing two scenarios)
```

## Some important info regarding tags
Note that the current version of the engine can only parse tags that are in text, headers, footers, and tables. text within images or text boxes will be ignored (we cannot parse it).



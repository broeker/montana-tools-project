---
title: 'Known issues' 
date: 2021-03-15 
permalink: /known-issues/index.html
eleventyNavigation:
  order: 12
  parent: Local setup and dev
  key: Known issues 
---
This is a list of known issues we uncovered during our last round of updates and fixes.

## Duplicate IDs (Radios - Chakra UI)

After an upgrade to Chakra v1.x we started seeing a large amount of console errors for duplicate IDs on radio buttons on the first page load. We have done some initial debugging, but so far cannot solve. It seems that it only happens when FieldRadio is wrapped inside of a FormGroup. See components/Fields/FieldRadio and components/Utils/FormGroup. We posted our results to the Chakra issue queue here, but so far no resposnes:

https://github.com/chakra-ui/chakra-ui/issues/3074

So far, the app seems to run fine with this error but we are hoping this will be fixed/addressed by Chakra at some point.


## Money formatting

During initial dev we never finalized how to handle money formatting+calculations. Currently, there are versions of the following functions scattered in the 4 processor files:

```
const format = number => {
  return Number(number).toLocaleString()
}
const unFormat = number => {
  var regex = /[.,\s]/g
  return parseInt(number.replace(regex, ""))
}
const unFormatMax = number => {
  return parseFloat(number.replace(/,/g, ""))
}
```

These need to be cleaned up and/or replaced with a single way of working with numbers/money throughout the processors.

## Frontend errors

EC fixed several know issues on the frontend; Droptica can report new errors as they arise and either fix or have EC assist. 

## CustomDrawer.js

The sidebar navigation was added late, as a proof-of-concept as the number of steps grew so large. It is currently messy but seems to be working, let us know if you see any issues that need fixing. 

components/utils/CustomDrawer.js

## PDF Formatting

We'll need to adjust the PDF output to match the sample doc (with $ signs and the appropriate number of decimal places as needed.)  The PDF file also seems to be generating a bunch of different font sizes that need to be adjusted, but have not yet tried to fixed on the Adobe site. 

## Financial Affadavit forms

We still need to upload and create an editable version of the Financial Affadavit forms. EC can get the initial file up on Adobe Cloud for editing.








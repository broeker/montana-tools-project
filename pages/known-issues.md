---
title: 'Known issues' 
date: 2021-02-05 
permalink: /known-issues/index.html
eleventyNavigation:
  order: 12
  parent: Local setup and dev
  key: Known issues 
---
This is a list of known issues we uncovered during our last round of updates and fixes.

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

I noticed about 5-6 places on the front end that need fixing/cleanup -- EC will take care of these and Droptica can report new errors as they arise.

**OtherJobs** -- the big one of these is that the app is currently skipping the "Do you have other jobs?" step for the primary application. We will investigate and fix.

## CustomDrawer.js

The sidebar navigation was added late, as a proof-of-concept as the number of steps grew so large. It is currently really messy, and contains some work-in-progress that needs cleaning up. EC can do this work if needed.

## PDF Formatting

We'll need to adjust the PDF output to match the sample doc (with $ signs and the appropriate number of decimal places as needed)

## Financial Affadavit forms

Currently for testing, we have commented out about 6-7 additional form pages that only concern the financial affadavit. We can re-add them once the Worksheet A is complete and we have a fillable PDF to work with for the affadavit form.

## Duplicate IDs

You will see a large amount of console warning for duplicate IDs -- these seems to be a problem with Chackra UI setup, and we will monitor this issue:

https://github.com/chakra-ui/chakra-ui/issues/3074







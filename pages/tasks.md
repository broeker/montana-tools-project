---
title: 'Tasks and to-dos' 
date: 2020-11-20
permalink: /tasks/index.html
eleventyNavigation:
  order: 5
  parent: Home
  key: Tasks and to-dos 
---
This outlines the high-level tasks we need completed. We can provide individual tickets as needed but this should provide a good overview.


## Overview 
* Finish the rest of the logic and processors for Worksheet A pdf generation -- Worksheet A is about 80% complete. We will need your help finishing the fillable PDF forms. 
* Start and finish the worksheet logic and processors for optional Worksheet B
* Start and finish the worksheet logic for "attachments" (used to expand answers that require an "other")
* Start and create logic and processors for the financial affadavit form [form](https://dphhs.mt.gov/Portals/85/csed/documents/financialaffidavit.pdf) in Acrobat so that it can be used for generating a PDF in functions/pdf-gen

## PDF gen
* Finish naming the fields in the fillable PDF Worksheet A (via Adobe Acrobat Cloud) as needed
* Import Worksheet B to Adobe Cloud and set it up as a fillable PDF
* Import a blank Attachments sheet to Adobe Cloud and set up as fillable
* See if we can figure out a method for seamlessly inserting the necessary attachments into a single PDF template. (e.g. combine Optional Worksheet B and any attachments into a single document)

## Other
* Make the currently hard coded values from the support guideline tables 1-3 into a configurable JSON file (currently hard-coded in process.js and percentages.js)
* Finish adding validation code throughout as needed --most validation can be "light" (as it is on the original site) and we can focus on critical fields
* Finalize a way to handle "numbers" in $ format for processing on the PDF i
* Finish hiding fields/steps that are only applicable to the financial affadavit and vice versa

## General bugs

* Tweak and adjust frontend UI as necessary for calculations (there are still a few places where the frontend may need adjustments)
* Fix and clean up logic in sidebar navigation -- this is a bit messy code but the idea is to have a consistent navigation that matches each step label

## Performance issues

As this form grew larger and larger, we began to experience performance issues. We have tried to optimize as possible using the Formiz docs, but the form still gets very slow depending on how many steps and fields end up at the end of the processs. We are hoping to find and easy way to solve this as part of this project. 

* Maybe we can break the form into separate sections, and store the data as localStorage until needed at the end? 
* Other ideas? 






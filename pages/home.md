---
title: Project overview 
date: 2020-12-09
permalink: /
eleventyNavigation:
  key: Home
  title: Project overview 
  order: 0
---
The following pages provide a technical overview and relevant background information for the Montana calculator project. This is a React-based project running on Gatsby that uses AWS Lambda serverless (using Netlify functions) to generate filled PDF forms based on user input.

![Home](/static/img/home_50.png)

## Current project status

**See:** [Montana Legal Help Tools](https://mlsa-tools.netlify.app/)

The code, structure, and overall framework for the project is already in place and large portions of the project are already complete (including the entire frontend and a large portion of the PDF generation.) We need help to bring it to completion. 

* The bulk of the remaining work can be completed by anybody with basic JavaScript skills and attention to detail
* Some of the work (such as a potential solution for performance) may require a more advanced engineer
* We have temporarily made the repository **public** so you can clone a copy as you prepare your estimate (see [local setup](/setup) here.)

## Key components

As you review the above URL you will see there are numerous pages and components to the website, but the two key components we need assistance with are described below. 

### 1. Child Support Calculator

https://mlsa-tools.netlify.app/child-support

This is the primary focus of the remaining work. The application is based on a previous website (see [key documents](/documents) for a link to the original) and is basically a clone of that existing application. The basic flow is as follows: 

* **Introduction** -- the first 10 steps of the app are split out into a separate component and lead the user through a series of info pages and instructions. *[This work is complete]*

![Interview](/static/img/interview_50.png)

* **Interview** -- when a user clicks "*start interview*," they have to accept a terms of use, and  then begin a very long interview process that takes them through up to around 30 different conditional steps. (This means that the "steps" are dynamic based on the users responses, the number of children they have, how many jobs they have, etc.)
  * Many individual steps also include conditional fields that respond based on input
  * The fields also change whether a user selects to create BOTH documents, or only one of the documents. (Much of this is not yet complete, and most fields are showing throughout for dev and testing purposes.)

![Interview](/static/img/interview2_50.png)

* **Generate docs** -- when the user finishes the interview, they get to a screen that lets them generate a PDF for download or print. (This is happening via a Netlify serverless function.) If necessary, a user can go back to any step in the process to fix information and then regenerate the docs for print or download.

![Generate](/static/img/generate_50.png)

This is the portion of the project where we need assistance, along with any necessary fixes in the frontend interview UI logic if needed. 

The basic code for PDF generation is in place, along with the initial fillable version of Worksheet A (this is currently complete through the SOLA section/Line 24 on Worksheet A.) To be completed are:

* Parenting days and annual child support portions of Worksheet A
* Worksheet B (a required worksheet for some users based on responses)
* Attachments (some responses, such as "other", require a blank attachment form. We do not yet have a template for this but can provide.)

(See more specifics in [tasks](/tasks))

### 2. Restitution Worksheet
https://mlsa-tools.netlify.app/restitution

This portion of the app shares the same tech stack and UI but it is an order of magnitude simpler. There are a lot less steps and conditionals, and only some very simple calculations. The front-end for this portion of the application is completely, but we do **NOT** yet have the fillable PDF that will be used to populate this data. We will provide this along with instructions for calculations. (These are mostly just adding up rows, etc.)

Unlike the Child Support Calculator, this is a greenfield form that does not have a state-generated PDF form like Worksheet A as an equivalent. Instead, we will create a simple PDF layout to insert the data in a series of simple rows and columns. 

* For now, you can estimate only the Child Support Calculator
* We will provide more details as needed for an estimate 

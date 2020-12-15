---
title: 'Code overview' 
date: 2020-11-20
permalink: /code/index.html
eleventyNavigation:
  order: 7
  parent: Home
  key: Code overview 
---
Here are a few shortcuts that will help understand the code and the tasks at hand:

## PDF gen 

```
functions/pdf-gen/pdf-gen.js
```

This is the main PDF generation function; it includes very little logic of its own but eventually will need adjusting to accommodate merging multiple PDFs (e.g. Worksheet A + B + any attachments). There is also no code yet for generating the Financial Affadavit.

## Processors

```
functions/pdf-gen/process.js
```

This is the parent processor file, and it calls individual processors from the same folder for each step in the process. This code is currently kind of messy but you can see the comments as to where it leaves off (at *sola.js*). 

Here is an example processor for calculating wages and mapping it to the right PDF field:

```
src/functions/pdf-gen/processors/income.js
```

Example:

```
const calcIncome = form => {
  // Total
  let data = []
  let totalPrimary = []
  let totalSecondary = []

  // Wages
  // TODO other jobs for both parents
  const primaryWages = calcWages(form, "EmploymentPrimary")
  data["income.mother.wages"] = Number(primaryWages).toLocaleString()
  totalPrimary.push(primaryWages)
  //console.log(totalPrimary)

  const secondaryWages = calcWages(form, "EmploymentSecondary")
  data["income.father.wages"] = Number(secondaryWages).toLocaleString()
  totalSecondary.push(secondaryWages)

  ...

```
::: callout
A significant portion of the project will be creating these remaining processors and mapping the correct fields to the fillable PDFs.
:::

## Entry point

The main entry point to the calculator lives here:

```
src/pages/child-support/calculator
```

This file sets up the page, and imports ALL of the individual form step components. There is some existing logic in this file to only show certain steps depending on which doc(s) you are creating. E.g.:

```
 <RulesProvider>
  <TermsOfUse />
  <InitiateInterview />
  <BasicInformation />
  <OtherParent />
  <NumberChildren />
  <EnterChildren />
  <OtherChildren />
  <EnterMyOtherChildren />
  {(documents === "both" || documents === "worksheets") && (
    <>
    <OtherChildrenSecondary />
    <EnterMyOtherChildrenSecondary />
    </>
   )}
   <Employment />
   <CurrentJob />
   <OtherJobs />
   ...
```

::: callout
This is where we are running into performance issues due to the large number of potential steps and fields.
:::


## Components

All of the individual form components live here:

```
src/components/ChildSupport
```

All of the *00-intro* components are complete and can be ignored. There are 31 individual components, a few with sub-components or files. 

Components *01-29* comprise each individual form step, and the logic and state for each field is self-contained.

The *Adminstrative Rules* component drives the rules that show up at bottom of each steo

The *CompleteApp* component drives the final step with the Generate button

## Field components

All of the Formiz fields components live here:

```
src/components/Fields/
```
They are used globally with both the child support calculator and the restitution worksheet. A typical example:

```
export const Employment = d => {
  const [state, setState] = useState({})
  let updateState = (name, value) => {
    setState({
      ...state,
      [name]: value,
    })
  }
  return (
    <FormizStep
      label="Your employment status"
      name="EmploymentStatus"
      order={7000}
    >
      <>
        <SectionHeader header={`Employment information`} />
        <FieldRadio
          name="EmploymentPrimary.initiate"
          placeholder="None"
          required="Required"
          label={"Do you have a job?"}
          updateState={updateState}
          options={[
            { value: "yes", label: "Yes" },
            { value: "no", label: "No" },
          ]}
        />
        {state["EmploymentPrimary.initiate"] === "yes" && (
          <FieldRadio
            name="EmploymentPrimary.initiateFulltime"
            placeholder="None"
            required="Required"
            updateState={updateState}
            label={"Is the job full time?"}
            options={[
              { value: "yes", label: "Yes" },
              { value: "no", label: "No" },
            ]}
          />
        )}

        ...
```

## Utilities

There are some key utility components here:

```
src/components/Utils/
```

These are used for some UI elements and to drive the "Add another?" functionality that appears in certain places of the app.
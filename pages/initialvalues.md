---
title: 'Working with initialValues' 
date: 2021-02-05 
permalink: /init/index.html
eleventyNavigation:
  order: 11
  parent: Local setup and dev
  key: Working with initial values 
---

Formiz recently added an initialValues method that allows us to prepopulate the form. Here is a short video explaining the current setup and issues: 

https://www.youtube.com/watch?v=nm0hVcryGKE&feature=youtu.be

## function/pdf-gen/processors/init.json

This is a sample data file we created that has values for all (or at least most) possible options. It is currently being used to pass into the main form, AND to pass into process.js for testing. This file can be updated as needed with sample data. 

## function/pdf-gen/processors/process.js

The init.json file is loaded into process.js and currently used as the basis for the form submission.

```
const init = require('./init.json')
...
// Pass hard-coded data to processors instead of form (init.json)
form = init
```

Normally in the real app, the processor will accept **form** data from calculator.js instead. 

See the video above as to why we are doing this work-around for now, instead of just passing the prepopulated form.

## /src/pages/child-support/calculator.js

For testing purposes, we also are passing **init.json** to the form to prepopulate it. 

```
import * as init from '../../../functions/pdf-gen/processors/init.json';
  <Formiz connect={form} onSubmit={handleSubmit}
      initialValues={ values }
```

However, as noted in the video above, this is not entirely functional because the form will NOT pick up data until the form field is visible. Because we are handling field visibility using React state, many of the fields are hidden and do not get re-populated until you manually trigger the field (e.g. change from "yes" to "no" and back). 

For the first several steps of the app, we fixed this by checking the initialValues form value in addition to the state, for example:

**InitiateInterview.js**

There are three possible hidden fields on this form, so I get the data from **form* values (if any)

```
 const formDocuments = (form.fields.Documents && form.fields.Documents.value)
 const formAction = (form.fields.Action && form.fields.Action.valued)
 const formLocation = (form.fields.Location && form.fields.Location.value)
```
Then add an additional OR clause checking for the existing state OR the form value:

```
  {(state.Action === "establish" || formAction === "establish") ? (
   <>
    <FieldInput
      name="CSED"
      label="If available, enter the District Court Case number or CSED Case number for the case in which you are seeking child support:"
      size={"xl"}
      fieldWidth={"10rem"}
      />
```
We didn't complete this effort throughout the app because it isn't clear if it will ultimately help development go faster, and some of the fields/pages (e.g. multiple checkboxes) may get a bit complicated.


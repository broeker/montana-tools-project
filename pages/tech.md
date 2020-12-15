---
title: 'Tec️h stack' 
date: 2020-11-20
permalink: /tech/index.html
eleventyNavigation:
  order: 10
  parent: Home
  key: Tec️h stack
---
This is the brief overview of the tech stack and the skills needed or best suited for this projects. The main thing will be understanding the Formiz (it is pretty simple) and the overall architecture of the forms steps + data processors + form generation:

## Formiz
https://formiz-react.com/
https://formiz-react.com/docs/getting-started

All of the form fields, engine and logic is using a React-based form engine called Formiz. We are using v1.0. Each step in form gets its own component, and all internal logic and state is handled per component. In a few cases, data is called from the formiz global store in order to have access to necessary global data for calculations. This approach was chosen to keep things as simple and isolated as possible given so many forms; **there is a performance concern** however as the number of fields and steps have grown. (See more in the tasks section)

## Gatsby
https://www.gatsbyjs.com/

The site itself runs on Gatsby but this is incidental to the work at hand. You'll need a basic understanding of Gatsby to run the site that is all. It was mainly chosen as a simple way to support the rest of the site (info pages, about, etc.)


## Backend
There is no backend, client-side only with serverless functions on Netlify (AWS Lamda) to handle the PDF generation. We are using a custom PDFKit binary, PDFiller for generation.


## Chakra-ui
https://chakra-ui.com/

We are using the Chakra-ui as a theme engine but probably only relevant if you need to make any adjustments to the form fields. 

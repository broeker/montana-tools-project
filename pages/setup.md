---
title: 'Local setup' 
date: 2020-11-20
permalink: /setup/index.html
eleventyNavigation:
  order: 10
  parent: Home
  key: Local setup 
---

**Repository: https://github.com/electriccitizen/mlsa-calculator**


In order have a local proxy server for Netlify functions to test the PDF generation, we use the Netlify CLI for local development. If you just want to run the site locally without a need to test the PDF generation, you can run:

```
git clone git@github.com:electriccitizen/mlsa-calculator.git

cd mlsa-calculator

npm run start 
```

If you to want to proxy the Netlify server for local PDF testing, install Netlify CLI:

* https://docs.netlify.com/cli/get-started/

and then run "netlify dev" instead of "npm run start"

```
netlify dev

** Access to Adobe Cloud

The current fillable PDF is managed in Adobe cloud and can be found locally at:

```
functions
  /pdf-gen
  mcsg-fillable.pdf
```

This is the PDF template used to generate the final user document. We will provide access to Adobe Cloud. About 80% of Worksheet A is complete, with work still need on Worksheet B and attachments.



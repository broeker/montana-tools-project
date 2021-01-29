---
title: 'Local setup and development' 
date: 2020-11-20
permalink: /setup/index.html
eleventyNavigation:
  order: 10
  parent: Home
  key: Local setup and dev 
---

**Repository: https://github.com/electriccitizen/mlsa-calculator**
**Branch:** main

## Netlify CLI

The project is hosted on Netlify, and we use the Netlify CLI to run local development in order to have a local proxy server for testing PDF generation. 

* Install instructions: https://docs.netlify.com/cli/get-started/

Once you have Netlify CLI installed you can spin up the project as follows:



```
git clone git@github.com:electriccitizen/mlsa-calculator.git

cd mlsa-calculator

netlify dev
```

This will spin up a localhost with hot reloading for development, and separate proxy server to mimic the AWS Lambda used for PDF generation so you can test that locally during development. 

### Add environment file to project root

Filename: 

```
.env.development
```

Add these two lines, update LAMBDA_TASK_ROOT to your project root:

```
LOCAL_ENV=true
LAMBDA_TASK_ROOT=/<path>/<to>/mlsa-tools
```


NOTEL If you just want to run the site locally without a need to test the PDF generation, you can run:

```
npm run start 
```

but you won't be able to test PDF generation.

## Development

You can do your development in your own droptica branch, or in multiple feature-based branches depending on your preference. We have set up automated branch deploys on Netlify. 

Any time a new branch is created, or when you push to an existing branch, it will automatically deploy those changes to a URL corresponding to your branch name. For example:

```
git checkout -b droptica

git push origin HEAD

```

This will automatically spin up a new site at: https://droptica--mlsa-tools.netlify.app/

Every time you push a change to your branch it will automatically deploy at that URL. Deploys typically take 60 seconds or less, and we can set up deploy Notifications for via email or Slack for you depending on preference.

## Updating main

When new features are complete they can be merged into main via Pull Request. For now I can review and accepts the PRs but if makes sense on your end we can also let you do your own merges into main as necessary. 

## Access to Adobe Cloud

You will need access to the fillable PDF on Adobe Cloud in order to help finish completing the remaining fields, and making adjustments as needed. The current fillable PDF is managed in Adobe cloud and can be found locally at:

```
functions
  /pdf-gen
  mcsg-fillable.pdf
```

This is the PDF template used to generate the final user document. We will provide access to Adobe Cloud. About 80% of Worksheet A is complete, with work still need on Worksheet B and attachments.



---
title: Publishing Gatsby site to AWS with AWS Amplify
category: Blog
cover: p2_4.png
author: Nader Dabit - Developer Advocate @AWS Mobile
---

In this post, we’ll walk through how to host & publish your next Gatsby site to AWS using AWS Amplify.

## Getting Started - Gatsby

First, install Gatsby CLI: `npm install - global gatsby-cli`

Next, create a new Gatsby site: `gatsby new my-gatsby-site`

Finally, change into the new site directory: `cd my-gatsby-site`

## Getting Started - AWS Amplify

Now that we have our Gatsby site up & running, let’s add hosting & make the site live on AWS.

First, install the AWS Amplify CLI: `npm i -g @aws-amplify/cli`

Then, configure AWS Amplify it with an IAM User: `amplify configure`

For a video walkthrough of how to configure the AWS Amplify CLI, click [here](https://www.youtube.com/watch?v=fWbM5DLh25U).  
Now, we can create a new Amplify project in the root of our Gatsby project:

`amplify init`

Now, the Amplify project has been created. You will see that you have a new amplify folder in your project directory as well as an _.amplifyrc_ file. Both of these contain your AWS Amplify project configuration.

Next, type command & see all of the options that we have: `amplify`

At the bottom, we can see the available categories available to us.

Now let's enable hosting: `amplify add hosting`

- Select the environment setup: _DEV_
- Hosting bucket name: gatsbyproj-20180808112129-hosting-bucket (or type whatever you’d like the bucket name to be)
- Now we can publish the app to AWS. To do so, we’ll run the following command:

`amplify publish`

Here, we’ll be prompted for the following: Are you sure you want to continue? _Y_

- Choose your default editor: _Visual Studio Code_
- Please choose the type of app that you’re building: _javascript_
- What JavaScript framework are you using: _react_
- Source Directory Path: _src_
- Distribution Directory Path: _public_
- Build Command: _npm run-script build_
- Start Command: _npm run-script develop_
- Do you want to use an AWS profile? _Y_
- Please choose the profile you want to use: _default_

Now, our resources will be pushed up to our account & our site will be published to a live url! What just happened? A few things:

- Amplify runs _npm run build_ to build a new distribution of your app
- A new S3 bucket is created in your AWS account
- All code in the public directory is uploaded to the S3 bucket
  We should have also be given the URL that the site is hosted on. At any time that we would like to get the url for our site, we can run:

`amplify status`

This command should give us all of the info about our app including the url of our website.  
If we ever want to configure the hosting setup, including adding Cloudfront, we can run:

`amplify configure hosting`

Here, we’ll be prompted for what we would like to change about the project configuration.

To learn more about AWS Amplify, check out the [Getting Started](https://aws-amplify.github.io/media/get_started) page.

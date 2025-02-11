# Text to Magic

This app is forked from the demo of Ankur, but i add WhatsApp as channel and translate to spanish 

In the end, you'll create a live web page that reacts to incoming whatsapp  with a fun animation on the screen. This combines Twilio's SMS and whatsapp product along with our serverless infrastructure to host the page.



![Demo](demo.gif)

## Pre-requisites

### Twilio Account

You'll need a Twilio Account for this project.. 

### Phone Number

Provision a phone number to use inside your Twilio Account following these steps: 

WhatsApp-->
## Deploying this project

### Step 1: Create a Function service.

Navigate to https://www.twilio.com/console/functions and click `Create Service`. Name this anything you'd like.

### Step 2: Update your Function service's environment.

In the service, find `Environment Variables` in the bottom-left side and set the following values:

| Variable              | Description | Required |
| :-------------------- | :----------------------------------------------------- | :-- |
| `TWILIO_PHONE_NUMBER` | Your Twilio phone number for whatsapp it should have the following structure whatsapp:+number in E.164 format | Yes |


### Step 3: Update your Function service's dependencies.

In the service, find `Dependencies` in the bottom-left side. Add the following dependency:

| Module              | Version |
| :-------------------- | :----------------------------------------------------- |
| `twilio` | * |

### Step 4: Upload all `/assets`

We need to upload our static files: the html, css, js, and json that powers this demo. 

1. Download this git repo.
2. In the service, click the blue `Add +` button, and then click `Upload File`.
3. Navigate to the `/assets` directory of this git repo and select all 4 of the files.
4. Set `index.html`, `style.css`, and `script.js` to `Public`. 
5. Set `studio.json` to `Private`. 
6. Click the blue `Deploy All` button in the bottom left corner.

### Step 5: Upload and run `setup.js`

We'll use a function called `setup.js` to auto-provision our Twilio account for the text-to-magic demo. This function will deploy a Twilio Studio Flow, configure your phone number, and configure Twilio Sync. 

1. In the service, click the blue `Add +` button, and then click `Add Function`.
2. Set the function name here to `setup.js`. 
3. Set the visibility by clicking beside the function name to `public`. 
4. Copy the contents from `functions/setup.js` to this file.
5. Click the blue `Save` button, then click the blue `Deploy All` button in the bottom left corner.
6. Click on `Copy URL` near the bottom-right of the function editor.
7. In a new tab, visit this `setup.js` URL once to run the function setup.

### Step 6: Upload `sync_token.js` and `post_magic.js`

1. Follow the steps previously to add `sync_token.js` and `post_magic.js` as `public` functions to your service. 
2. It is not necessary to visit these functions from your browser as in the 6th/7th step previously. 
3. Cick the blue `Deploy All` button in the bottom left corner.

## Go Live!

That's it! You are now ready to test out your own text-to-magic demo. Navigate to the `index.html` Asset from within the Function service. Click `Copy URL` and visit it in a new tab. Text in to your number and watch the magic happen!

## Extras

### Bonus: Modify the Studio Flow
The setup function we ran earlier created a [Twilio Studio](https://www.twilio.com/console/studio) Flow which asks the user to send in some magic. You can edit this flow to control the conversation accordingly.

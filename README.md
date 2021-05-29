# Integrate-with-Machine-Learning-APIs-Challenge-Lab

Integrate with Machine Learning APIs: Challenge Lab
1 hour 30 minutes
9 Credits
Rate Lab
GSP329
Google Cloud Self-Paced Labs

Overview
In a challenge lab you’re given a scenario and a set of tasks. Instead of following step-by-step instructions, you will use the skills learned from the labs in the quest to figure out how to complete the tasks on your own! An automated scoring system (shown on this page) will provide feedback on whether you have completed your tasks correctly.

When you take a challenge lab, you will not be taught new Google Cloud concepts. You are expected to extend your learned skills, like changing default values and reading and researching error messages to fix your own mistakes.

To score 100% you must successfully complete all tasks within the time period!

This lab is recommended for students who have enrolled in the Integrate with Machine Learning APIs quest. Are you ready for the challenge?

Topics tested

Grant the service account admin privileges for BigQuery and Cloud Storage.

Create and download a service account credentials file to provide Google Cloud credentials to a Python application.

Modify a Python script to extract text from image files using the Google Cloud Vision API.

Modify a Python script to translate text using the Google Translate API.

Check which languages are in the extracted data by executing a BigQuery SQL query.

Setup
Before you click the Start Lab button
Read these instructions. Labs are timed and you cannot pause them. The timer, which starts when you click Start Lab, shows how long Google Cloud resources will be made available to you.

This Qwiklabs hands-on lab lets you do the lab activities yourself in a real cloud environment, not in a simulation or demo environment. It does so by giving you new, temporary credentials that you use to sign in and access Google Cloud for the duration of the lab.

What you need
To complete this lab, you need:

Access to a standard internet browser (Chrome browser recommended).
Time to complete the lab.
Note: If you already have your own personal Google Cloud account or project, do not use it for this lab.

Note: If you are using a Pixelbook, open an Incognito window to run this lab.

How to start your lab and sign in to the Google Cloud Console
Click the Start Lab button. If you need to pay for the lab, a pop-up opens for you to select your payment method. On the left is a panel populated with the temporary credentials that you must use for this lab.

Open Google Console

Copy the username, and then click Open Google Console. The lab spins up resources, and then opens another tab that shows the Sign in page.

Sign in

Tip: Open the tabs in separate windows, side-by-side.

If you see the Choose an account page, click Use Another Account. Choose an account
In the Sign in page, paste the username that you copied from the Connection Details panel. Then copy and paste the password.

Important: You must use the credentials from the Connection Details panel. Do not use your Qwiklabs credentials. If you have your own Google Cloud account, do not use it for this lab (avoids incurring charges).

Click through the subsequent pages:

Accept the terms and conditions.
Do not add recovery options or two-factor authentication (because this is a temporary account).
Do not sign up for free trials.
After a few moments, the Cloud Console opens in this tab.

Note: You can view the menu with a list of Google Cloud Products and Services by clicking the Navigation menu at the top-left. Cloud Console Menu
Challenge scenario
You have started a new role as a member of the Analytics team for Jooli Inc. You are expected to help with the development and assessment of data sets for your company's Machine Learning projects. Common tasks include preparing, cleaning, and analyzing diverse data sets.

You are expected to have the skills and knowledge for these tasks, so don't expect step-by-step guides to be provided.

Your challenge
You have been asked to develop a process to analyze sets of images of signage to extract and translate any text in the images. This extracted text information will be used to help classify the images as part of a machine learning project that will use this image dataset for model training and evaluation. The images all contain text, but the text may be in any language. The images are stored in a Cloud Storage bucket that has been provided for you.

You must use a Python script to process each of the image files by sending them to the Google Vision API to identify the text in the image. The text from each image must be saved back to files on Cloud Storage, with a separate file for the text from each image. If the text locale is not English (locale='en'), you must then send the text to the Google Translate API to get an English translation for the original text. Once all of the images have been processed, the script must upload the results to a BigQuery table.

This diagram outlines the process: ml-apis-challenge-diagram.png

The processed text data must then be written out to a pre-existing BigQuery table called image_text_detail in a dataset in your project called image_classification_dataset.

A colleague on your team had started to work on the code to process the images based on a Python script previously used to process a set of text files using the Natural Language API. Your colleague has been moved to a separate project and you must now complete the task.

Most of the work on the script has been completed and the version you have been given will access a storage bucket, and iterate over every image file it finds. However the specific API calls that need to be made to find the text in each image and then send that text to the Translation API have not yet been implemented.

You have been given a copy of the work in progress Python script and a set of sample images in a Cloud Storage bucket that is named after your lab Project ID.

Your colleague identified the unfinished parts of the script and commented on the API calls that need to be made. There are three unfinished parts in the script that you must complete to make the correct Machine Learning API calls. All of them are preceded with a comment using the label # TBD:. The final line of code uploads the result data to BigQuery. In the script, this line is disabled by a comment character. When you are satisfied that the rest of the script is working, remove the comment character to enable the final line.

Before you work on the script, you must prepare your environment by creating a service account with the correct permissions and download the credential file for that account. Once you have the service account credentials, you can modify the Python script and use it to process the image files.

To complete the challenge, the original extracted text, locale, and translated text data for all of the images must be loaded into the BigQuery table called image_text_detail. The code to do this is in the script but you must remove the comment characters to enable the line of code at the end of the script.

Once you have successfully processed the image files using the updated Python script and uploaded to data to BigQuery, you must confirm that image data has been successfully processed by running the following Query in BigQuery:

SELECT locale,COUNT(locale) as lcount FROM image_classification_dataset.image_text_detail GROUP BY locale ORDER BY lcount DESC
This query will report the number of signs of each language type it has found in the set of sample images.

Task 1: Configure a service account to access the Machine Learning APIs, BigQuery, and Cloud Storage
Create a new service account that provides credentials for the script. Once you have created the account, bind the BigQuery Admin and Cloud Storage Admin roles to the Service Account to provide the IAM permissions required to process files from Cloud Storage and insert the result data into a BigQuery table.
Check that a service account exists that has admin permissions to access BigQuery and Cloud Storage

If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Task 2: Create and download a credential file for your Service Account
When you have configured the service account permissions, download the JSON format IAM credentials file for the service account. Don't forget to configure the environment variable that supplies the name of the credential file for the Python script.
Check that an IAM credential file has been created for the service account

If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Task 3: Modify the Python script to extract text from image files
Copy the file analyze-images.py from the Cloud Storage bucket that was created for you into the Cloud Shell. You must modify this Python script to extract text from the image files stored in your project bucket and then save the text data for each file into a text file that is written back to the same bucket. Remember, the parts of the script where you need to add in the code to access the APIs are marked with the comment # TBD.

After you modify the first part of the script to use the Cloud Vision API to extract text data from the image files, you should run the partially completed script to check your progress to make sure you are on the right track.

Confirm that the application can extract text from images
If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Task 4: Modify the Python script to translate the text using the Translation API
Now modify the second part of the Python script to identify any non-English text data found by the Vision API and use the Translation API to translate the original text into English.

Confirm that the application can translate text and store the results in BigQuery
If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Task 5: Identify the most common non-English language used in the signs in the data set
After you update the script to successfully find and translate the text in the images, remove the comment character from the line at the end of the script that uploads the data to BigQuery. When the data has been uploaded to BigQuery, confirm that all necessary data has been loaded into BigQuery by running a query that counts the number of times it sees each separate language.
Run a BigQuery query to report how often each language has been found in the images

If you don't get a green check mark, click on the Score fly-out on the top right and click Check my progress on the relevant step. A hint pop up opens to give you advice.
Tips and Tricks
Tip 1. You do not need to provide any specific permissions to a service account to access most of the Google Machine Learning APIs such as the Google Cloud Vision and Translation APIs. The Python script does need permissions to access BigQuery and to create objects in Cloud Storage. The easiest way to do that is to bind the service account to roles/bigquery.admin and roles/storage.objectAdmin.

Tip 2. You must set an environment variable to provide the details of the credentials file that should be used by the Python script to access the Google Cloud APIs.

Tip 3. You can find details about the Vision API Client document_text_detection API call in the Python API Documentation reference page for the Vision API Client and the details of the Vision API annotation response object in the Python API Documentation reference page for the Vision API Objects

Tip 4. For details about the Translation API Client translate API call, see the Python API Documentation for the Translation V2 API Client

Congratulations!
You have developed a process to analyze images of signage and extract and translate the text in the images.

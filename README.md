# flask_5_tailwind
HHA504 / Cloud Computing / Assignment 5 / Video Hosting, Flask App &amp; Cloud Deployment

This repo aims to provide hands-on experience in video hosting, creating a Flask app styled with Tailwind CSS, and deploying it to a cloud platform. CDN services in Google Cloud or Azure are leveraged to optimize video delivery. 

## This repo contains the following: 
+ **screen_record** folder: contains an mp4 file of a recording of the flask app deployment using Azure App Services.
+ **screenshots** folder: contains screenshots of the flask app web page, video file served from the CDN, and the video CDN endpoint on Azure. Also includes a screenshot of the flask app opened on a phone, indicating its responsive design across different device sizes. 
+ **templates** folder: contains the html file required for the flask application.
+ **README.md** file: contains an overview of the repo.
+ **app.py** file: contains the code for deploying the application.
+ **requirements.txt** file: contains elements required to deploy the flask application on Azure.

# Documentation 
## 1. Video of Application
**Flask App Link**: https://video-cdn.azurewebsites.net 

https://github.com/c-susan/flask_5_tailwind/assets/123512714/fb55a3cb-7cf9-49c7-b957-5ec296f0723b

## 2. Cloud CDN & Video Hosting
The video is hosted on Azure using Storage Accounts. To hpst the video, I went through the following steps: 
1. Signed into Azure 
2. In the search bar on the homepage, search "Storage accounts" and click on the service. 
3. On the top left-hand side of storage accounts, clicked to create a new storage account with: resource group, account name, and **Standard** performance. 
4. Once the new accounted is deployed, in the overview section, clicked the **Security** link to enable the following: secure transfer, allow blob, allow storage account key access and saved the changes. 
6. On the menu on the left side of the storage account menu menu, clicked **Containers** under **Data Storage**. 
7. Created a new container with **Anonymous Access Level = Container (anonymous read access level)**. 
8. Uploaded a video file into the new container. 
9. In the overview of the storage account (left-hand side), **Security + Networking > front door and cdn**: Created a new endpoint with **Service Type = Azure CDN** and **Query string caching behavior = Ignore Query String**. 
10. In the new created endpoint, opened the **Endpoint hostname** link in a new tab. 
11. In Azure, went back to the video upload located in the storage account container (Data Storage > Containers):
      +  clicked onto the video upload and opened the url in a new tab
      +  in the video upload url, copied everything after ```.net/```. 
12. Went back to the tab with the endpoint: pasted in what I copied into the url, making sure there was a backslash after ```.net```. I made sure to paste this new url somewhere so it can be used to create the flask application.

## 3. Flask App with Tailwind CSS
In my google shell environment, I created a script to create a basic Flask application using Tailwind CSS to style a video player interface that embeds my hosted video. Code is also added to make sure the application is responsive across various device sizes. 

## 4. Cloud Deployment
Before deploying the application on a cloud service, created a ```requirements.txt``` file to contain the python packages used in my script. I deployed the application using Azure App Services with the following steps: 
1. In the google shell terminal, installed the Azure CLI using the command: ```curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash```.
2. To test that it was correctly installed, ran ```az```.
3. Ran ```az login --use-device-code``` and followed the directions from the output.
4. Typed ```az webapp up --resource-group <resource-group> --name <app-name> --runtime PYTHON:3.9 --sku B1``` to create a new app service. Replaced <resource-group> with my resource group name and <app-name> with my app name.
5. Waited for the deployment to be completed and accessed the link to the website in azure. 






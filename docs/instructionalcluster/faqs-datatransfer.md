---
layout: default
title: Unprotected Large Data Transfer
parent: Frequently Asked Questions
grand_parent: Instructional Cluster
nav_order: 4
description: ""
permalink: /instructionalcluster/faqs/datatransfer
---

# Unprotected Large Data Transfer

## Upload to Google Drive
When uploading large datasets to notebook instances, the process may timeout. In this case, it is recommended to upload your file into Google Drive and download it from the terminal in Jupyter Notebooks.


1. Use the **New** button in the top left corner of Google Drive to upload your file. <br/><br/>
![Google Drive Upload](/images/instructionalcluster/faq-datatransfer1.png) <br/><br/>
1. In the file's **Share** option, access will be restricted by default. To change this, select **Anyone with a link** from the dropdown menu. This will allow file access via Jupyter Notebook's terminal later. <br/><br/>
![Share Access](/images/instructionalcluster/faq-datatransfer2.png)<br/><br/>
1. Click the **Download** button to bring up the "Google Drive - Virus scan warning" screen. <br/>
### Screen Opens in Separate Tab <br/>
If this screen automatically opens in another tab: <br/><br/>
![Virus scan warning (Separate Tab)](/images/instructionalcluster/faq-datatransfer3.png) <br/><br/>
Then, append `&confirm=yes` to the end of the URL in the search bar, save it, and skip to step 4. <br/><br/>
### Screen Opens as Pop-up <br/>
If the "Google Drive - Virus scan warning" window opens within the same tab: <br/><br/>
![Virus scan warning (Same Tab)](/images/instructionalcluster/faq-datatransfer4.png) <br/><br/>
Then:
    - Copy/paste the file's share link in the search bar <br/><br/>
    ![URL View Mode](/images/instructionalcluster/faq-datatransfer6.png) <br/><br/>
    - Locate/copy the file ID in the URL <br/><br/>
    ![File ID in URL](/images/instructionalcluster/faq-datatransfer7.png) <br/><br/>
    - Combine that ID with these URL parameters <br/><br/>
        ![URL Download Mode](/images/instructionalcluster/faq-datatransfer9.png) <br/><br/>
        `https://drive.google.com/u/0/uc?id={REPLACE WITH ID}&export=download&confirm=yes`<br/><br/>
1. Once the proper URL is obtained, the file can be downloaded into your Jupyter Notebook through the integrated terminal. Use the <a href="https://www.gnu.org/software/wget/" target="_blank">wget</a> command, the URL to your Google Drive file, and wget's `-O` option to download the file under a specific name in your current directory. <br/>

{: .note }
You can start a new terminal session by clicking the blue "+" button in the sidebar of your Jupyter Notebook, then selecting **Terminal** to start a new terminal session. 

Command template: 
```
  $ wget "https://example.url" -O {exampleFileName.tar.gz}
```
Example: 
```
 $ wget "https://drive.google.com/u/0/uc?id=160dDIhVQLNkUgBgaSIMxuJz0WKoDowyv&export=download&confirm=yes" -O nih.tar.gz
```
Check download:
```
  $ ls -la
```

![Download in Terminal](/images/instructionalcluster/faq-datatransfer5.png)

{: .note }
If the dataset is sensitive or protected, email **itd-research.ci@sdsu.edu** to evaluate more secure options for transferring research data.

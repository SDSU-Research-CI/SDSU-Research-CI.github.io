---
layout: default
title: Getting Access
parent: Software Factory
nav_order: 2
description: ""
permalink: /softwarefactory/gettingaccess
---

# Getting Access
In order to run containers on the Instructional Cluster, you will need an account with the National Research Platform and you will need to be added to a namespace. A namespace allows its members to share access to containers, enabling collaboration.

In addition to the written directions below, we've recorded a video walkthrough for [getting an account and requesting access to a namespace](https://mediasite.sdsu.edu/Mediasite/Play/8e7f235bc56f44fdb4586cffe1e477a71d).

## Creating a National Research Platform Portal Account
The National Research Platform (NRP) portal will automatically create you an account once you login with your SDSUid. Follow these steps to sign into the NRP portal:

1. Navigate to [https://portal.nrp-nautilus.io/](https://portal.nrp-nautilus.io/)
1. Click Login in the top right corner
  - ![Nautilus Portal webpage](/images/softwarefactory/gettingaccess1.png)
1. You will be greeted by a CILogon page
  - ![CILogon webpage](/images/softwarefactory/gettingaccess2.png)
1. Click the dropdown in the Identity Provider section and search for "San Diego State University"
  - ![Search San Diego State University](/images/softwarefactory/gettingaccess3.png)
1. Click the checkbox for "Remember this selection"
  - ![Check remember this selection](/images/softwarefactory/gettingaccess4.png)
1. Click Log On
  - ![Log on](/images/softwarefactory/gettingaccess5.png)
1. You will be greeted by the SDSU Login page
  - ![SDSU Login page](/images/softwarefactory/gettingaccess6.png)
1. Enter your SDSU credentials
  - ![SDSU credentials](/images/softwarefactory/gettingaccess7.png)
1. Click Login
  - ![SDSU Login](/images/softwarefactory/gettingaccess8.png)
1. Complete the DUO MFA (this example used a DUO Push Notification)
  - ![DUO Push Notification](/images/softwarefactory/gettingaccess9.png)
1. You should now be redirected to the NRP Portal and you should see your SDSUid in the top right corner
  - Note: You may not see as many options in the top navigation, as the screenshot below is from an admin account
  - ![Signed in NRP Portal](/images/softwarefactory/gettingaccess10.png)

Congratulations! You now have an NRP account and you're one step closer to running containers.

### NRP Portal tasks:
1. [Peruse the namespaces](https://portal.nrp-nautilus.io/namespaces-g)
    - It may be easiest to use your browser's find tool (ctrl + f / cmd + f)
    - Search for "sdsu-" to see SDSU related namespaces
        - ![SDSU Namepaces](/images/softwarefactory/gettingaccess12.png)

1. [Download your kube config](https://portal.nrp-nautilus.io/authConfig)
    - You will need to sign in with CILogon again
    - The file should download and you should see the following screen
        - ![kube config file](/images/softwarefactory/gettingaccess13.png)
    - Open your terminal and run the following command:
        - `mkdir ~/.kube`
    - Copy your config file into the ~/.kube folder (replace the path below for your config file):
        - `cp ~/Downloads/config ~/.kube/config`
    - Check to make sure your config file copied successfully:
        - `ls ~/.kube`

## Requesting Access to a Namespace
Now that you have signed into the NRP Portal, the Research and Cyberinfrastructure team can add you to a namespace which will allow you to run containers on the Instructional Cluster.

Submit the [Research Cyberinfrastructure Consultation](https://sdsu.service-now.com/sp?id=sc_cat_item&sys_id=029639611bb825505764fd1b1e4bcb3a&sysparm_category=29ac153fdbbf4c9024094672399619e9) ServiceNow form with the following:
1. Request Type should be "Software Factory Containerization"
2. In the "Please provide a description of your request" indicate the name of the namespace you want created, or specify an existing one you wish to be added to
    - Note: All namespaces will be pre-fixed with "sdsu-"
3. Click Request

![Research Cyberinfrastructure Consultation Form](/images/softwarefactory/gettingaccess11.png)

After you submit the form a member of the Research and Cyberinfrastructure team will follow up and add you to the desired namespace.

## Next Steps
Once you have an NRP account and have been added to a namespace, continue to the [Getting Started page](./gettingstarted) to run your first container on the Instructional Cluster.
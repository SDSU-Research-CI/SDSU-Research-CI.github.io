---
layout: default
title: Fixing Connection Refused
parent: Frequently Asked Questions
grand_parent: Instructional Cluster
nav_order: 3
description: ""
permalink: /instructionalcluster/faqs/connectionrefused
---

# Fixing Connection Refused
Have you encountered an error message like this and are unable to get to the Instructional Cluster?

![Connection refused](/images/instructionalcluster/faq-connectionrefused1.png)

Sometimes a network error may occur while accessing our JupyterHub instance, so here a few things to try to troubleshoot the issue.

## Try another Browser
If time is of the essence, try opening [https://jupyterhub.sdsu.edu/](https://jupyterhub.sdsu.edu/) in a different browser, if you have another browser installed already.

## Open In Private or Icognito Tab
If you don't have a second browser available, or are attached to a specific browser, then you can try opening a private or igcognito tab.

## Flush DNS Cache - Advanced
If the above options didn't work for you, then you can try to flush your browser's DNS (Domain Name Service) cache. 
- Note: This will increase your page load times to sites, thus why this is a last resort.

1. Open a new tab
2. Copy and paste the page URL for your browser's DNS settings page
- |Browser | Page URL|
  |:-------|:--------|
  |Chrome | chrome://net-internals/#dns|
  |Edge | edge://net-internals/#dns|
  |Firefox | about:networking#dns|
3. Search the page for a button along the lines of "Clear Cache"
  - ![Clear Cache](/images/instructionalcluster/faq-connectionrefused2.png)
4. Click the button
5. Close and re-open your browser
6. Try signing in again at [https://jupyterhub.sdsu.edu/](https://jupyterhub.sdsu.edu/)

If that doesn't work, then please let your instructor know and ask them to report the issue to Research and Cyberinfrastructure.

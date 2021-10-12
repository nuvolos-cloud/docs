# RStudio

## Recovering an unresponsive RStudio session

In certain cases RStudio sessions can become unresponsive, due to large amounts of output printed or large amount of data loaded. If restarting the application in Nuvolos doesn't resolve the issue, you can follow the below steps to reset the session state:



1. Stop the RStudio app if running
2. Create a quick snapshot in Nuvolos sidebar (hover on the camera icon and click "Quick Snapshot")
3. On the sidebar go to files area and in the dropdown on the top select "Personal" (by default "Workspace" will be shown)
4. Toggle to show hidden files
5. Navigate to the folder .local/share
6. Rename the rstudio folder (click on the 3 dots on the right when hovering the rstudio folder and select "Rename") to rstudio.bak
7. Launch Rstudio

{% hint style="info" %}
For some previous RStudio versions, the sessions might be stored in the folder .rstudio instead of .local/share/rstudio. In this case rename this folder as described in step 6.
{% endhint %}

If you continue to experience issues, please reach out to our support team through the messenger inside Nuvolos.

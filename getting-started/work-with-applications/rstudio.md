# RStudio

## Recovering an unresponsive RStudio session

In certain cases RStudio sessions can become unresponsive, due to large amounts of output printed or large amount of data loaded. If restarting the application in Nuvolos doesn't resolve the issue, you can follow the below steps to reset the session state:



1. **Stop the RStudio app** if running (hover on the Rstudio icon on the sidebar and click 'Stop')
2. **Create a quick snapshot** in the Nuvolos sidebar (hover on the camera icon and click "Quick Snapshot"). You do not need to open this snapshot, it only serves as a backup.
3. On the sidebar **go to files area** and in the dropdown on the top **select "Personal"** (by default "Workspace" will be shown)
4. Toggle to **show hidden files**
5. Navigate to the folder **.local/share**
6. **Delete the rstudio folder** (click on the 3 dots on the right when hovering the rstudio folder and select "Delete")
7. **Launch Rstudio**

{% hint style="info" %}
For some previous RStudio versions, the sessions might be stored in the folder .rstudio instead of .local/share/rstudio. In this case delete this folder as described in step 6.
{% endhint %}

If you continue to experience issues, please reach out to our support team through the messenger inside Nuvolos.

## RStudio is responsive but it doesn't accept commands

If you can interact with the RStudio window (menu items are working, dropdowns open, etc.) but commands you try to run in R will not execute, it might be that the R console is showing a plus sign at the start of the line:

![R waiting for further input](<../../.gitbook/assets/Screenshot 2021-10-31 103625.png>)

If this is the case, R is waiting for further input. As you can see in the above example, a curly brace was open, and R waits the curly brace to be closed for the expression to be complete (and executable).

If you want to cancel the statement, make sure to focus on the R console in RStudio by clicking on it, then hit the Escape button on your keyboard.

![After the cancelled statement](<../../.gitbook/assets/Screenshot 2021-10-31 103918.png>)

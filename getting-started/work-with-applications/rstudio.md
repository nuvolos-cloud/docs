# RStudio

## Recovering an unresponsive RStudio session

In certain cases RStudio sessions can become unresponsive, due to large amounts of output printed or large amount of data loaded. If restarting the application in Nuvolos doesn't resolve the issue, you can follow the steps in the [Troubleshooting Applications](troubleshooting-applications.md#clearing-user-application-settings) guide to clear the application state.

## RStudio is responsive but it doesn't accept commands

If you can interact with the RStudio window (menu items are working, dropdowns open, etc.) but commands you try to run in R will not execute, it might be that the R console is showing a plus sign at the start of the line:

![R waiting for further input](<../../.gitbook/assets/Screenshot 2021-10-31 103625.png>)

If this is the case, R is waiting for further input. As you can see in the above example, a curly brace was open, and R waits the curly brace to be closed for the expression to be complete (and executable).

If you want to cancel the statement, make sure to focus on the R console in RStudio by clicking on it, then hit the Escape button on your keyboard.

![After the cancelled statement](<../../.gitbook/assets/Screenshot 2021-10-31 103918.png>)

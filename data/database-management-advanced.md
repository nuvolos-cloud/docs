---
description: Nuvolos supports advanced data manipulation requirements via SQL IDEs.
---

# Database management \(advanced\)

For users who require advanced database management capabilities, we offer DBeaver as an integrated Nuvolos application.

You can add DBeaver by selecting the option 'Other applications' when creating a new Nuvolos application. The connection to Nuvolos is automatically configured in DBeaver, however the first time you connect to Nuvolos, DBeaver will prompt to install the relevant database driver \(Snowflake\), which needs to be approved.

For more information on DBeaver, please visit: [https://github.com/dbeaver/dbeaver/wiki](https://github.com/dbeaver/dbeaver/wiki)

### Collaborating in DBeaver

Inside the DBeaver application, there is a Project called General \(the default DBeaver project\). In the Scripts folder, you will find that the files area is linked in, so scripts saved to /files are automatically visible to all users of DBeaver inside an instance.

When creating new scripts, if you would like it to be accessible for other users in the instance, please save it under the 'files' folder. If you save it simply to the 'Scripts' folder, then it will be only accessible to your own user, which can be useful when prototyping.




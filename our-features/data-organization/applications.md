# Applications

## Overview

With Nuvolos, users will be able to work with their data and files using the latest technological frameworks such as Jupyter lab, Rstudio, Matlab, Stata, Spyder, and Sas.

Users with an editor role in an instance will be able to create and work with applications.

## Features

* **Containerized:** every single application in Nuvolos is _containerized_. Containerization involves bundling an application together with all of its related configuration files, libraries, and dependencies required for it to run across different operating systems. This implies that applications are isolated and independent from each other.  Initially, each application will contain the exact default configuration, libraries, and dependencies. Once created and started, the user will be able to install new packages and libraries in an application. It is important to keep in mind that what the user installs in one application will not be install for other applications, even if they are similar. For example, if the user creates a Jupyter Lab application \(App1\) and installs the new packages A and B, and then creates another Jupyter Lab application \(App2\), then App2 will _NOT_ have packages A and B. 
* **Distributable:** The configuration files and libraries of an application can be distributed to the current state of other instances. This facilitates the dissemination of teaching material or results. 
* **Simple:** Creation of a snapshot requires one simple operation; Nuvolos ensures the completeness of the operation, and the end-user does not have to tally each step required.


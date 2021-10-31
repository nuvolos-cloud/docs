# States and snapshots

## Overview

Nuvolos supports reproducible research and safe work organization by guaranteeing that a state of a research project can be immutably saved and restored at will.

Each instance consists of _states_. A state is a collection of data, code and applications at a given point in time. The _current state_ is the only mutable state: it is the only state in an instance that can be modified. Working in the current state, you can upload, delete, rename, and work with files and tables, as well as create and start applications. \
\
Other states are called _snapshots. _A snapshot is an immutable state. Snapshots can be created of the current state.

## Features

* **Complete:** A snapshot encompasses all relevant information of the state of a research project for complete reproducibility. Not only data and code are saved, but also applications and their software dependencies.\

* **Restorable:** A snapshot can be restored to be the current state, and Nuvolos ensures that the restored state will be consistent with previous behaviour of the same state.\

* **Distributable:** A snapshot can be distributed to the current state of other instances. This facilitates the dissemination of teaching material or results.\

* **Simple:** Creation of a snapshot requires one simple operation; Nuvolos ensures the completeness of the operation, and the end-user does not have to tally each step required.

## Access control

On each structural level of Nuvolos, a variety of user roles are defined to control access and possible actions of users.&#x20;

Access control of snapshots is controlled on the _instance_ level. The following rules hold:

* The current state can only be modified by users who are _instance editors_.
* The snapshots can be viewed by _instance viewers_.
* Applications can only be run in the _current state_. Consequently, only instance editors can run applications in an instance.

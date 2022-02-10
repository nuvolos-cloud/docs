# Setting up a custom .bashrc

In instances **created after 2022-02-08**, you have the support for defining your own [.bashrc](https://www.journaldev.com/41479/bashrc-file-in-linux), which is persistent between restarts.

In Nuvolos, the \~/.bashrc file is generated automatically, and is tailored for each application. While you can edit this file, the changes will be lost once the application is restarted.

If you wish use a persistent .bashrc, please define one at

```
/files/.bashrc
```

The system will automatically source the above file when opening a new shell session.

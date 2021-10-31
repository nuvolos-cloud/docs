# High-performance computing

If a given computation requires a large number of CPUs or memory (RAM), it is possible to **scale **the application to a **dedicated high-performance compute node**. In this case, the same application will launch with the exact same interface, however, the available resources can be significantly larger (e.g. up to 120 vCPU and 456GB memory) or can include additional devices (e.g. a GPU).

{% hint style="warning" %}
Application scaling is charged against the credits of the underlying account and is directly based on the amount of application runtime. Please turn off the scaled application if you no longer require the larger resources and relaunch it without scaling when the baseline resources are sufficient (e.g. investigating outputs).

For long-running jobs, you can also rely on the** **[**automated inactivity stopper**](../getting-started/work-with-applications/long-running-applications.md) to handle application stops. The automated inactivity stopper will shut down the application if it is not using at least half of a single vCPU for computation and it is not opened in Nuvolos for at least 6 hours.
{% endhint %}

### How to scale your app

Scaling can be done inside Nuvolos by hovering on the application icon once it has been launched and clicking the 'Scale' button. High-performance computing integration needs to be enabled for this to be possible, please reach out to support using Intercom or by e-mail if you require assistance with this.

![](../.gitbook/assets/scale\_app\_ed.gif)

### Application-specific notes

#### Rstudio

For Rstudio we recommend using the 'Local Jobs' feature to run the jobs in the background, this way you can submit multiple jobs whilst also making sure the job continues to run if you navigate away from Rstudio, without blocking the interface.

![](<../.gitbook/assets/image (3).png>)

[Learn more about local jobs in Rstudio](https://github.com/rstudio/webinars/blob/master/74-background-jobs/slides.pdf) &#x20;

#### JupyterLab

If running notebooks via Jupyter, we recommend submitting the notebooks for computation using [papermill](https://papermill.readthedocs.io/en/latest/) and specifying an explicit logfile when executing from the Jupyter terminal. This way you can disconnect from the Jupyter application and the notebook execution can continue whilst be able to monitor run progress.

```
papermill --stdout-file /files/my_job.out --stderr-file /files/my_job.err NOTEBOOK_PATH [OUTPUT_PATH]
```

#### MATLAB

MATLAB constructs like [parfor ](https://www.mathworks.com/help/parallel-computing/parfor.html)can be leveraged on scaled applications using local [parallel pools](https://www.mathworks.com/help/parallel-computing/parpool.html). \
Nuvolos will configure MATLAB to use the appropriate number of CPUs after a scaling operation, so you can start your parpool simply with the command:

```
pp = parpool('local');
```

The pool will be deleted after 30 minutes of idle time or with an application restart. To delete it manually, use

```
pp.delete()
```



&#x20;

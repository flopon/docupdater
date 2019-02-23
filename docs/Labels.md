Label on container or service can override the default behavior.

You can use the LABEL instruction on the Dockerfile or add label on the run command:
`
docker run -it -d --label docupdater.disable=true docupdater/docupdater
`

See this example of stack file to add a label on a service (swarm):
```
version: "3.6"

services:
  docupdater:
    image: docupdater/docupdater
    deploy:
      labels:
        docupdater.disable: "true"
```

***

* Labels
  * [Disable update](#disable-update)
  * [Enable update](#enable-update)
  * [Latest](#latest)
  * [Stop signal](#stop-signal)
  * [Notifiers](#notifiers)
  * [Template file](#template-file)

***

### Disable update
**Label:** `docupdater.disable`  
**Example:** `docupdater.disable: "true"`  

Disable update for the service or container.

### Enable update
**Label:** `docupdater.enable`  
**Example:** `docupdater.enable: "true"`  

When docupdater is start with option [--label](Options.md#Label), this label enable update for container or service.

### Latest
**Label:** `docupdater.latest`  
**Example:** `docupdater.latest: "true"`  

With this label, the container or service will always pull the latest tag.

### Stop signal
**Label:** `docupdater.stop_signal`  
**Example:** `docupdater.stop_signal: 1`  

Define a stop signal to send to the container instead of SIGKILL. Can be string or int.

### Notifiers
**Label:** `docupdater.notifiers`  
**Example:** `docupdater.notifiers: ""`  

This override the default notifiers. You can disable notification for a specific container or service to set the label to an empty value (like the example).

### Template file
**Label:** `docupdater.template_file`  
**Example:** `docupdater.template_file: "/template.j2"`  

That override for this container or service the notification message to use. See [notifications docs](Notifications.md).
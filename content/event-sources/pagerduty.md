---
type: "page"
creatordisplayname: "Rob Barnes"
creatoremail: ""
lastmodifierdisplayname: "Rob Barnes"
lastmodifieremail: ""
title: "PagerDuty"
weight: 10
---

If configuring PagerDuty as the event source, you will need the follow things configured in order for Rift to work:

- A PagerDuty API token for Rift to use.
- A webhook notification configured with the following custom headers:

## PagerDuty API token

In order to generate an API token for PagerDuty, folllow the [official PagerDuty documentation.](https://support.pagerduty.com/docs/api-access-keys#generate-a-general-access-rest-api-key) This will be needed when configuring Rift in the testing step.
## Configuring the webhook

1. From the PagerDuty Web UI, navigate to the Integrations tab and click on `Generic Webhooks (v3)`

![step 1](/event-sources/images/pd-step1.png?classes=shadow "")
2. Select `+ New Webhook`

![step2](/event-sources/images/pd-step2.png?classes=shadow "")
3. Enter the Rift URl in the webhook form and select the service your would like PagerDuty to send notifications for. Select the following events for the webhook:
    - `incident.acknowledged`
    - `incident.resolved`

![step3](/event-sources/images/pd-step3.jpeg?classes=shadow "")
4. Click on `Add custom header` and add the following headers to the webhook:
    - `X-Boundary-Project` - This is the Boundary project ID that contains the hosts and targets associated with this service in PagerDuty
    - `X-Boundary-Targets` - This is a comma separated list of Boundary targets associated with this service in PagerDuty.
Click on `Add Webhook` to save this configuration.

![step4](/event-sources/images/pd-step4.png?classes=shadow "")
5. A notification will appear with a Webhook verification secret that Rift will require. Keep a note of this secret as this will be needed for the Rift configuration when testing.

![step5](/event-sources/images/pd-step5.png?height=300px&classes=shadow "")

## Testing the webhook

In order to test the webhook notificaton, you will need to get Rift up and running.

1. Create a configuration file using the [Rift configuration guide](/rift-configuration). You will need the PagerDuty webhook secret and the PagerDuty token for this step
2. Follow the steps in the [Boundary configuration guide](/boundary)
3. Start the Rift server using the platform of your choice. For the binary version, run the following command:

```sh
rift -config-file=config.json
```

_**NOTE:** This assumes the `config.json` file is in the current working directory_
4. In the PagerDuty Web UI, navigate back to the Webhook you just created and click on the `Send Test Event` button.
![step1](/event-sources/images/pdtest-step1.png?classes=shadow "")

You should see the following output in the Rift logs.

![step2](/event-sources/images/pdtest-step2.png?classes=shadow "")

### PagerDuty Connectivity to Rift

In order for PagerDuty to send webhook notifications to Rift, Rift will need to be accessible. If running Rift as localhost without a public IP address, you will need to put a public proxy in front of it. [Ngrok](https://ngrok.com/) works well for local testing.

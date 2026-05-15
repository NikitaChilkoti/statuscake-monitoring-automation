## Incident simulation

Up until now, everything has behaved nicely.

The monitor was created successfully, uptime checks were working, and the API responses looked healthy. Which is good… but also slightly suspicious.

Because monitoring systems become truly useful only when something actually breaks.

And honestly, that’s the entire point of this phase. Instead of waiting for a real outage, we’ll intentionally stop the service and observe how the monitoring system reacts.

---

## Step 1 - Verify the Service

Before breaking anything, first confirm the application is running properly.

If using Nginx:

```
sudo systemctl status nginx
```

You should see: ```active (running)```

Also verify:

* the website opens in the browser
* the StatusCake monitor currently shows `UP`

At this stage, the system is healthy and the monitor is confirming that correctly.

---

## Step 2 - Stop the Service

Now let’s intentionally take the application down.

Run:

```
sudo systemctl stop nginx
```

And with this the application disappears from the internet.

---

## What Happens Next?

Interestingly, nothing changes immediately. And that’s important to understand.

Monitoring systems work on intervals. StatusCake waits for the next scheduled check, tries reaching the application again, and only then marks the service as unhealthy.

So for a few moments:

* the application is already down
* but the monitor still shows healthy

---

## Step 3 - Observe the Monitor

Open the StatusCake dashboard and wait for the next monitoring cycle.

After a few minutes, the monitor should transition from: ```UP```

to:  ```DOWN```

Because now the outage is no longer hidden. The monitoring system has officially detected the failure.

---

## Step 4 - Validate Through API

Now verify the same thing using Bash.

Run:

```bash
curl -X GET "https://api.statuscake.com/v1/uptime" \
-H "Authorization: Bearer $STATUSCAKE_API_TOKEN" \
-H "Content-Type: application/json" | jq
```

Inside the response, the monitor status should now reflect the outage correctly.

---

## Step 5 - Restore the Service

Now bring the application back online.

```bash
sudo systemctl start nginx
```

Verify again:

```bash
sudo systemctl status nginx
```

Expected result:

```text
active (running)
```

After the next monitoring cycle, StatusCake should detect the recovery and change the monitor status back to: ```UP```

Which confirms:

* outage detection worked
* recovery detection worked
* monitoring visibility behaved correctly

---

## This simulation was tiny.

But even here, you can already notice something interesting:

* applications fail instantly
* monitoring reacts slightly later
* recovery takes time to validate

Reducing those delays is a huge part of reliability engineering.

---

## Now that outages can be detected properly, the next step is turning monitoring data into operational reports.

So, we'll do reporting-automation.md

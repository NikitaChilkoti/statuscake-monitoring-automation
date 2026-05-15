# 03 - Create Monitor Automation

## Context

Most of the setup preparations till this point are done, including,
* API token
* Bash environment
* authentication testing

Now comes the interesting part…

Actually creating monitors automatically.

Because creating one monitor manually is fine.

Creating:

* production monitors
* staging monitors
* API checks
* internal dashboards

again and again?

That gets repetitive. And repetitive is boring, right?

---

# So, what's the approach?

The script will:

* send an API request to StatusCake
* create a new uptime monitor
* return monitor details automatically

Simple idea.

---

# Step 1 - Create Script

Inside the `scripts/` directory:

```
touch create-monitor.sh
```

Open the script:

```
nano create-monitor.sh
```

---

# Step 2 - Add Script Content

```
#!/bin/bash

API_URL="https://api.statuscake.com/v1/uptime"

curl -X POST "$API_URL" \
-H "Authorization: Bearer $STATUSCAKE_API_TOKEN" \
-H "Content-Type: application/x-www-form-urlencoded" \
-d "name=production-nginx-monitor" \
-d "website_url=https://example.com" \
-d "check_rate=300"
```

---

# What This Script Does

This sends a request to StatusCake saying:

```
“Create a monitor called production-nginx-monitor
and check the website every 5 minutes.”
```

That’s it.

And weirdly enough…
that small API request replaces an entire manual setup flow.

---

# Step 3 - Make Script Executable

```
chmod +x create-monitor.sh
```

Without this:

* Bash sees the file
* but refuses to execute it

---

# Step 4 - Run the Script

```
./create-monitor.sh
```

---

# Expected Result

If everything works:

* StatusCake returns JSON response
* monitor gets created successfully
* uptime checks begin automatically

You can verify this from:

* StatusCake dashboard
* API response output

---
Now, monitoring is updated, instead of:

* clicking buttons manually

the workflow becomes:

* scriptable
* repeatable
* scalable

And this is how many operational tools work.
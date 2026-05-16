By now, monitors are active, outages can be detected, and recovery validation works properly. Which honestly already feels much more operational than simply creating a few uptime checks manually.

But repetitively opening dashboards for every small verification is so much time taking. 
Teams usually want something quicker a small summary showing whether services are healthy or not.
Right here reporting automation starts becoming useful.

---

Instead of manually checking StatusCake every time, the idea now is to generate lightweight monitoring summaries directly from Bash.

---

## Step 1 - Create the Script

Inside the `scripts/` directory:

```touch generate-report.sh```

Open the file:

```nano generate-report.sh```

---

## Step 2 - Add the Script

```
#!/bin/bash

API_URL="https://api.statuscake.com/v1/uptime"

echo "===== Monitoring Report ====="
echo ""

curl -s -X GET "$API_URL" \
-H "Authorization: Bearer $STATUSCAKE_API_TOKEN" \
-H "Content-Type: application/json" | jq '.data[] | {
    name: .name,
    status: .status
}'
```

---

### What will happen with this?

The script sends a request to the StatusCake API, fetches monitor data, and then uses `jq` to display only the important information instead of dumping the entire JSON response into the terminal.

---

## Step 3 - Make It Executable

```chmod +x generate-report.sh```

---

## Step 4 - Run the Script

```./generate-report.sh```

You should now see a small monitoring summary directly inside the terminal.

Something like:

```
{
  "name": "production-nginx-monitor",
  "status": "up"
}
```

See, how useful it is already.

With this Bash scripts can access the data, process it, summarize it, and eventually even trigger actions automatically.

---

The final phase focuses on future improvements and how this setup could evolve into a larger monitoring and incident automation system.
That's future-improvements.md

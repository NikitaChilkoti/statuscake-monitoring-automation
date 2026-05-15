## Context

Before automating anything, the scripts first need a way to communicate with StatusCake itself.

That means:

* generating API credentials
* testing authentication
* verifying that Bash can successfully interact with the API

---

## Step 1 - Create a StatusCake Account

Create a free StatusCake account.

Once logged in:

* open the dashboard
* navigate to API settings

I will add the screenshot here.

---

## Step 2 - Generate API Token

Inside the dashboard:

* create an API token

This token will later allow:

monitor creation, monitor deletion, status checks, automation workflows

---

## Always remember this

Never EVER hardcode API keys directly into scripts.

Because eventually:
The scripts get pushed, repos become public, and secrets will accidentally leak.

I and you are working on a small monitoring project, let's not make it a a security lesson for now, right?

---

## Step 3 - Store API key securely

Inside the terminal:

```bash
export STATUSCAKE_API_TOKEN="your_api_token"
```

Verify variable:

```bash
echo $STATUSCAKE_API_TOKEN
```

---

## Step 4 - Install jq

The API responses return JSON data.

And though Bash can display it, but it won't make it look better.

So, to make it easy to read, and a no mess...

Install jq:

```
sudo apt install jq -y
```

---

## Step 5 - Test First API Request

Run:

```bash
curl -X GET "https://api.statuscake.com/v1/uptime" \
-H "Authorization: Bearer $STATUSCAKE_API_TOKEN" \
-H "Content-Type: application/json"
```

---

## Expected Result

If authentication succeeds:

* JSON monitor data appears
* API connection is working

Even if no monitors exist yet, that is completely fine.

This is the interesting part about APIs.

The moment authentication works:

* dashboards become programmable
* repetitive tasks become scriptable
* operational workflows become automatable.

---

## Current Progress

At this stage:

* API authentication works
* Bash can communicate with StatusCake
* Linux environment is ready
* automation setup can begin

Now the project moves to actual operational scripting.

---
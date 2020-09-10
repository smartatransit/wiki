Feedback Service
================

The feedback service is for collecting user feedback and outage reports. It exposes two endpoints: one for saving a new piece of feedback, and another health check endpoint that's used internally to trigger outage alerts.

### Save Feedback Endpoint

`POST feedback.smartatransit.com/v1/feedback`

Request body:
```
{
	"kind": "outage | comment | service_condition",
	"value": "positive | negative | neutral",
	"message": "string",
	"email": "string"
}
```

Response body: none.

The endpoint saves the feedback to the database, along with some information from the authorization token.

### Health Check Endpoint

`POST feedback.smartatransit.com/v1/health`

Request body: none.

Response body:
```
[
	{
		"name": "string",
		"description": "string",
		"healthy": "boolean",
		"metadata": "any"
	},
	...
]
```

The endpoint returns any relevant statuses, including the health of dependencies (like the databese connection) and elevated rates of outage reports.

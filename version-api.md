---
description: This page contains the docs for our Version API
---

# Version API

## Public API:

The 3 GET requests below are public, and don't need any authentication.

{% api-method method="get" host="http://updates.sbdplugins.nl:3222" path="/api/v2/plugins" %}
{% api-method-summary %}
Get plugins
{% endapi-method-summary %}

{% api-method-description %}
Get all the plugins
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Everything is ok.
{% endapi-method-response-example-description %}

```javascript
[
    {
        "id": 1,
        "name": "ActionFoto",
        "version": "1.2"
    },
    {
        "id": 2,
        "name": "ThemeParkPlus",
        "version": "3.1"
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://updates.sbdplugins.nl:3222" path="/api/v2/plugins/:id" %}
{% api-method-summary %}
Get plugin by ID
{% endapi-method-summary %}

{% api-method-description %}
Get a plugin by the ID
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Everything is ok. If you get an empty response, there is no plugin with this ID.
{% endapi-method-response-example-description %}

```javascript
{
    "id": 1,
    "name": "ActionFoto",
    "version": "1.2"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://updates.sbdplugins.nl:3222" path="/api/v2/download/:id" %}
{% api-method-summary %}
Download a plugin by ID
{% endapi-method-summary %}

{% api-method-description %}
Download a plugin by the ID
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="port" type="string" required=true %}
The port of your server
{% endapi-method-parameter %}

{% api-method-parameter name="license" type="string" required=true %}
The license of your product
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Everything is ok. You will receive the plugin as an JAR.
{% endapi-method-response-example-description %}

{% code title=":id.jar" %}
```

```
{% endcode %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


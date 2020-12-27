---
description: This page contains the docs for our Version API
---

# Version API

## Public API:

The 3 GET requests below are public, and don't need any authentication.

{% api-method method="get" host="https://updates.sbdplugins.nl" path="/api/v2/plugins" %}

{% api-method method="get" host="https://updates.sbdplugins.nl" path="/api/v2/plugins/:id" %}

{% api-method method="get" host="https://updates.sbdplugins.nl" path="/api/v2/download/:id" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="license" type="string" required=true %}
The license of your product
{% endapi-method-parameter %}

{% api-method-parameter name="port" type="string" required=true %}
The port of your server
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Everything is ok. You will receive the plugin as an JAR.
{% endapi-method-response-example-description %}

{% code title=":id.jar" %}
```text

```
{% endcode %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


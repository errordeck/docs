# Sentry

You can use Sentry's SDKs with Errordeck, to send errors to Errordeck. You can read more about Sentry [here](https://sentry.io/welcome/).

## How to use Sentry with Errordeck

You would need to use a different DSN. You can get your full DSN in your project settings in the dashboard. An example of a DSN would look like this:

```bash
https://<secret>@app.errordeck.com/<project>
```

## Supported SDKs
We know that Errordeck support at least these languages:
* Javascript
* Python
* Ruby
* Crystal
* PHP

But we should work with most sentry client support, except for those sending dumps.

## Sentry python example

```python
import sentry_sdk
from sentry_sdk.integrations.django import DjangoIntegration

sentry_sdk.init(
    dsn="https://<secret>@app.errordeck.com/<project>",
    integrations=[DjangoIntegration()]
)
```
And then you can use the sentry_sdk as usual.

Example of a simple error:
```python
from sentry_sdk import capture_exception


def foo():
    bar()


def bar():

    try:
        baz()
    except Exception:
        capture_exception()
```



---
sidebar_position: 4
---

# Error

On Errordeck, errors are the main thing. You can see all errors sent to Errordeck in the dashboard.

An error combines a title, description, environment, platform, stacktrace and tags. The central part of the error is the title, description, and stacktrace. We group errors by title and description, meaning it will be grouped if you send an error with the same title and description.

You can browse the previous errors for an error that was grouped. You can also see the stacktrace of the error and the environment, platform, and tags of the error.

## What is different about Errordeck errors

We have a few unique features that make Errordeck different from other error-tracking tools, and we will explain them in this section.

### Do not save user context

Errordeck does not save user context. This means that while others error-tracking servers keep user data like email and names, Errordeck does not hold any user data in the error data. This is made actively to make Errordeck more privacy friendly. We recommend sending internal ids instead of user emails and names, and they can be sent as a tag.

We use sentry's user context to count unique users. We use the data sent in there to create a hash, and then the context is thrown away. This means that sending the same user context multiple times will be counted as one user. This is made to ensure we only count the same user multiple times.


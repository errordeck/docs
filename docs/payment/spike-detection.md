---
sidebar_position: 5
---

# Spike Detection

Spike detection is a feature that is used to detect spikes in the number of errors. We use standard deviation to detect spikes. If the number of errors is more than 2 standard deviations from the mean, it will be considered a spike. We will not count spikes in the number of errors, that we use to maybe ask you to upgrade your plan. You can read more about standard deviation [here](https://en.wikipedia.org/wiki/Standard_deviation).

Spike detection is to be nice to our users. We do not want to charge them for spikes in the number of errors. We want to make sure that they are not charged for errors that are not their fault.
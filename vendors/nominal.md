# Overview

[Nominal](https://nominal.io/) is a data-focused vendor that offers a data engineering platform for analyzing and monitoring telemetry from hardware engineering and test.

## Key Features

* **[Nominal Core](https://nominal.io/products/core)**: Data insights platform that warehouses telemetry, video, logs, and sensor data. Has dashboards for visualization of data, and analysis. Most likely some elastisearch, or an indexed lakefs store for blob data + apache spark for analysis, and some dashboarding software for visualization. Data appears to be organized using tags, potentially uses Open Telemetry (OTEL) to unify data. A key use-case is running very data-intensive jobs without running out of memory, so spark or some other hadoop-distributed compute might be used. Another key use case is aggregating data from various sources.

* **[Nominal Connect](https://nominal.io/products/connect)**: Edge compute platform that connects more directly to test data. Appears to act as a liasion to ingest raw data, transform into some format, then push to Nominal Core. Also includes visualization of the test equipment. Direct competitor to labview. Enables execution of test procedures, and direct connection to DAQs, jacks, serial, etc.

## SDK

[Nominal SDK](https://nominal-io.github.io/nominal-client/reference/toplevel/). Contains getters and setters to create a report procedure, such as `add_dataset`, `add_video`, and `execute` using the `Run` class. The Nominal platform appears to take the python code and will execute the job (probably in spark).



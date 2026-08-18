# Python Logging Basics

## The `logging` Module

Python's built-in `logging` module provides a structured way to record events that occur while a program is running.

```python
import logging
```

Unlike `print()`, logging supports:

* Log levels
* Timestamps
* Multiple output destinations
* Configurable formatting
* Persistent log files

## Basic Logging

A simple configuration can be created with:

```python
logging.basicConfig(
    level=logging.INFO,
    format="%(levelname)s: %(message)s"
)
```

Then messages can be recorded with:

```python
logging.info("Operation completed.")
logging.warning("Something unusual happened.")
logging.error("Operation failed.")
```

Example output:

```text
INFO: Operation completed.
WARNING: Something unusual happened.
ERROR: Operation failed.
```

## Log Levels

Logging levels describe the severity or purpose of a message.

### `DEBUG`

Used for detailed diagnostic information.

```python
logging.debug("Current value: 42")
```

### `INFO`

Used for normal program activity.

```python
logging.info("File processed successfully.")
```

### `WARNING`

Used when something unusual happens but the program can continue.

```python
logging.warning("Destination already exists.")
```

### `ERROR`

Used when an operation fails.

```python
logging.error("Unable to open file.")
```

### `CRITICAL`

Used for very serious failures that may prevent the program from continuing.

```python
logging.critical("Application cannot continue.")
```

The common severity order is:

```text
DEBUG
INFO
WARNING
ERROR
CRITICAL
```

## Logging Level Filtering

The configured logging level determines which messages are shown.

For example:

```python
logging.basicConfig(level=logging.INFO)
```

will normally display:

```text
INFO
WARNING
ERROR
CRITICAL
```

but not:

```text
DEBUG
```

## Formatting Log Messages

Logging output can include additional information.

For example:

```python
logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s"
)
```

Possible output:

```text
2026-08-18 20:30:12,415 - INFO - Operation completed.
```

Common formatting fields include:

```text
%(asctime)s
```

Timestamp.

```text
%(levelname)s
```

Logging level.

```text
%(message)s
```

The log message.

## Handlers

Handlers determine where log messages are sent.

A single logging system can send the same log record to multiple destinations.

### `StreamHandler`

Sends logs to a stream, usually the terminal.

```python
logging.StreamHandler()
```

### `FileHandler`

Writes logs to a file.

```python
logging.FileHandler(
    "application.log",
    encoding="utf-8"
)
```

Both handlers can be used together:

```python
logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s",
    handlers=[
        logging.FileHandler(
            "application.log",
            encoding="utf-8"
        ),
        logging.StreamHandler(),
    ],
)
```

Now the same message can appear both in the terminal and in the log file.

## Logging vs `print()`

`print()` is useful for simple output and debugging.

```python
print("Processing complete.")
```

Logging is more suitable when the program needs structured information about its execution.

```python
logging.info("Processing complete.")
```

Logging provides:

* Severity levels
* Persistent history
* Timestamps
* Multiple output destinations
* Better control over what is displayed

## Logging Operation Results

Logging works especially well when functions return information about whether an operation succeeded.

For example:

```python
success = perform_operation()

if success:
    logging.info("Operation completed.")
else:
    logging.warning("Operation was skipped.")
```

This keeps responsibilities separated:

```text
Function
→ performs the operation
→ returns the result

Caller
→ decides how to report the result
```

## Key Idea

Logging is not simply a more complicated version of `print()`.

Its purpose is to create a structured record of program behavior.

As programs become larger or interact with external systems, logging becomes increasingly useful for:

* Debugging
* Monitoring
* Error investigation
* Understanding program execution
* Keeping a permanent operation history
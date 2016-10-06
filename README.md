# InfluxDB output plugin for Embulk

## Overview

* **Plugin type**: output
* **Load all or nothing**: no
* **Resume supported**: no
* **Cleanup supported**: yes
* **Dynamic Database creating**: yes
* **Dynamic Series creating**: yes

## Configuration

- **host**: hostname (string, default: localhost)
- **port**: port number (integer, default: 8086)
- **username**: username (string, default: 'root')
- **password**: password (string, default: 'root')
- **database**: database name (string, required)
- **series**:    series name (string, required) (can use column value placeholder. see example)
- **mode**:     "insert", or "replace". See bellow. (string, default: insert)
- **timestamp_column**: timestamp column (string, default: nil)
- **ignore_columns**: ignore column names (array[string], default: [])
- **tag_columns**: tag column names (array[string], default: [])
- **default_timezone**: default timezone for column (string, default: 'UTC')
- **time_precision**: time precision (string, default: 's')

### Modes

* **insert**:
  * Behavior: This mode inserts rows simplly.
* **replace**:
  * Behavior: Same with insert mode excepting that it drops the target series first.

## Example

```yaml
out:
  type: influxdb
  username: root
  password: root
  database: dbname
  series: ${key_name}_series
  tag_columns: [name]
  timestamp_column: day
  mode: replace
  ignore_columns:
    - key_name
```

## ToDo
- column_options support

## Build

```
$ rake
```

# Events Hugo Module

(intro)

## Requirements

Requirements:
- Go 1.14
- Hugo 0.61.0


## Installation

If not already, [init](https://gohugo.io/hugo-modules/use-modules/#initialize-a-new-module) your project as Hugo Module:

```
$: hugo mod init {repo_url}
```

Configure your project's module to import this module:

```yaml
# config.yaml
module:
  imports:
  - path: github.com/theNewDynamic/hugo-module-tnd-events
```

## Usage

## Date Handling

In order to not use default `date` parameter to assign start and end times for the events, we'll use `time_start` and `time_end`. For Hugo to pick `time_start` as the effective date of an event you need to add this to your project configuration:

```
frontmatter:
  date:
  - time_start
  - :default
```

### Some Partial/Feature

#### Examples

### Settings

Settings are added to the project's parameter under the `tnd_events` map as shown below.

```yaml
# config.yaml
params:
  tnd_events:
    [...]
```

#### Configure Key 1

#### Configure Key 2

#### Defaults

ld copy/paste the above to your settings and append with new extensions.

## theNewDynamic

This project is maintained and loved by [thenewDynamic](https://www.thenewdynamic.com).

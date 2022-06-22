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

## Events

Events are content files of the type `event`. They need in their front matter
- __title__\*: String
- __date__: A Datetime
- __time_start__ A datetime. (if not set, will use __date__)
- __time_end__ A datetime.

## Venues
Venues are either content files or front matter maps entered for each events.

Venues can either be content files or Maps set to the events front matter. They should be structured this way:

- __name:__\* String (if content file, `.Title` will be used)
- __address:__ A string. Ex: 7301 S. Sante Fe Drive
- __city:__ A string. Ex: Littleton
- __state:__ A string. Ex: CO
- __country:__ A string. Ex: USA
- __zip:__ A string or int Ex:'80120'
- __phone:__ A string Ex: +1 555 5555
- __link:__ A string Ex: https://church-corner.org
- __tickets_link:__ A string Ex: https://church-corner.org


### Venues as content files.
If venues are used as content files, Events should refer to them with their path relative to the content directory of the project.

```yaml
# content/event/church-concert.md
title: Church Concert
time_start: 2021-11-22T17:30:08-05:00
time_end: 2021-11-22T20:30:08-05:00
venue: venue/church-at-the-corner.md
```

### Venues as maps.

Venues can also directly be entered as Front Matter maps

```yaml
# content/event/church-concert.md
title: Church Concert
time_start: 2021-11-22T17:30:08-05:00
time_end: 2021-11-22T20:30:08-05:00
venue:
  name: Church At The Corner
  address: 1 Corner Street
  city: Angleville
  state: Texas
  zip: '89989'
  link: https://church-corner.org
  phone: '+1 555 5555'
```

### Settings

Settings are added to the project's parameter under the `tnd_events` map as shown below. (Entered are defaults)

```yaml
# config.yaml
params:
  tnd_events:
    venue_key: venue
    date_formats:
      datetime: January 2, 2006 at 3:04 pm
      date: 'January 2, 2006'
      time: '3:04 pm'
```

#### venue_key
The front matter key used in content files to identify the venue either as a path pointing to a content file
or as a strucured map

#### date_formats

Date formats are used to format dates throughout the view files.

## AddToCal

The Events module uses TND's AddToCal module to generate an "Add to calendar" button lists the following services:
- Google
- Yahoo
- iCal
- Outlook

## theNewDynamic

This project is maintained and loved by [thenewDynamic](https://www.thenewdynamic.com).

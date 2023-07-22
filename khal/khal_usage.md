# Khal - Usage

## Topic

|   | sections                    | sub-sections                        |
| - | -                           | -                                   |
| 1 | [Agenda](#agenda)           |                                     |
| 2 | [Event Today](#event-today) |                                     |
| 3 | [New Event](#new-event)     | [single cli](#single-cli)           |
|   |                             | [interactive cli](#interactive-cli) |
| 4 | [Interactive](#interactive) |                                     |


## Agenda

```bash
khal calendar
```

## Event Today

```bash
khal list today
```

> will indicate with tomorrow event if events available

## New event

### Single CLI

```bash
khal new
```

### Interactive CLI
```bash
khal new -i
```

## Interactive

```bash
khal interactive
```

or

```bash
ikhal
```


1. move to specific date and press <kbd> Enter </kbd>

2. press <kbd> n </kbd> to create new event

3. edit with normal keyboard without vi-mode

create/modify event keys (no vi-mode):

  | keys                                  | description                    |
  | :-:                                   | :-:                            |
  | <kbd> Tab </kbd>                      | swap to next                   |
  | <kbd> Shift </kbd> + <kbd> Tab </kbd> | swap to previous               |
  | <kbd> Esc </kbd> + <kbd> Esc </kbd>   | to quit                        |
  | <kbd> Tab </kbd> (s)                  | swap to `> Save` to save event |


[^1]: `khal new --help`: review more informations for new event.

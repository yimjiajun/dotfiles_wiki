# cron - Format

```
* * * * * <command>
| | | | |
| | | | +---- Day of the week (0 - 6) (Sunday to Saturday, 7 is also Sunday on some systems)
| | | +------ Month (1 - 12)
| | +-------- Day of the month (1 - 31)
| +---------- Hour (0 - 23)
+------------ Minute (0 - 59)
```

**1\. `*`: *any* or *every* value for specific time field**

- example:
  - `0` `*` `*` `*` `*`: every 1 hour (at minute 0)

**2\. `*/<num>`: *every* specific time filed**

- example:
  - `*` `*/2` `*` `*` `*` : every 2 hours

**3\. Schedule command will not source *.bashrc***

> ensure not using aliases or function defined in .bashrc

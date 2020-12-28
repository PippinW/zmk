# Building ZMK for the Rebound 4-3

Some general notes/commands for building the Montsinger Rebound from the assembly documentation.

## Encoder Notes

If you built your Rebound without encoders, you'll need to change the following in your local Rebound config or add them to the end of the file.

```
CONFIG_EC11=n
CONFIG_EC11_TRIGGER_GLOBAL_THREAD=n
```


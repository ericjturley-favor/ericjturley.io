# Structured/JSON logging
Running a Micronaut app locally, by default, will give you structured, json logging:

<img width="743" alt="image" src="https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/41db4343-1aac-42ae-afae-df237689650a">

# Change it to human-readable
Add this to your "Run Configuration"...

![image](https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/3f912aae-bf1e-4b8d-9f9c-70f568ec8281)
![image](https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/38898f40-b338-4db3-81c5-b6714ed82aed)

```MICRONAUT_ENVIRONMENTS=local```

To see human-readable logging:

<img width="749" alt="image" src="https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/5d05f9ac-af04-4a8d-b26d-e5aabe0ece42">

# Caveat
With this simple step, you're omitting the MDC (Mapped Diagnostic Context) from the logging.

## Can I have both?
If you want the MDC data AND human-readable logs locally, you'll need 
* to KNOW what objects/fields in the MDC you want to see
* to adjust the appender pattern

You can read more here: 
* https://logback.qos.ch/manual/mdc.html
   * Search for `%x`
* https://www.baeldung.com/mdc-in-log4j-2-logback

Example from the logback docs:
```
<appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender"> 
  <layout>
    <Pattern>%X{first} %X{last} - %m%n</Pattern>
  </layout> 
</appender>
```

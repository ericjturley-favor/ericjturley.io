# Local Micronaut Logging

## Structured/JSON logging
Running a Micronaut app locally, by default, will give you structured, json logging:

<img width="743" alt="image" src="https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/41db4343-1aac-42ae-afae-df237689650a"/>

## Change it to human-readable
Add this to your "Run Configuration"...
{collapsible="true"}
: ![image](https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/3f912aae-bf1e-4b8d-9f9c-70f568ec8281)
: ![image](https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/38898f40-b338-4db3-81c5-b6714ed82aed)

> `MICRONAUT_ENVIRONMENTS=local`
> {style="note"}

in order to see human-readable logging like this:

<img width="749" alt="image" src="https://github.com/ericjturley-favor/ericjturley.io/assets/137823129/5d05f9ac-af04-4a8d-b26d-e5aabe0ece42"/>

## Add the entire missing MDC

With the previous step, you're omitting the MDC (Mapped Diagnostic Context) from the logging.

Credit: @kwhiteside-favor:

You can add <code>%mdc</code> to your pattern to get it. Here's an example you can append to your existing log pattern:
```
 MDC: %mdc%n
```
{ignore-vars=true}

### Or add specific values
If you want specific MDC data AND human-readable logs locally, you'll need 
* to KNOW what objects/fields in the MDC you want to see
* to adjust the appender pattern

You can read more here: 
* <a href="https://logback.qos.ch/manual/mdc.html">logback mdc docs</a>
   * Search for <code>%x</code>
* <a href="https://www.baeldung.com/mdc-in-log4j-2-logback">a baeldung article</a>

Example from the logback docs:
```xml
<appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender"> 
  <layout>
    <Pattern>%X{first} %X{last} - %m%n</Pattern>
  </layout> 
</appender>
```
{ignore-vars=true}

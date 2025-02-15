<center><h1>Flags</h1></center>
<center>
<p>Flags, flag arguments, and everything else about flags!</p>
</center>

---

# Flags
Flags, if you didn't already know, when in commands are typically short identifiers that convey bits of information
or mark what certain arguments are going to be explicitly. It's useful for controlling lots of optional arguments.
In commands, the argument would be the `-n` part of `/example flag -n=3`.

## Example of Registering Flags
```java
@Command("example")
public class Command {
    
    @SubCommand("flag")
    @CommandFlags({@Flag(flag = "n", longFlag = "num", argument = int.class, suggestion = "[<number>]")})
    public void example(Sender sender, Flags flags) {
        flags.getValue("n").ifPresent(arg -> {
            int num = Integer.parseInt(arg);
            ...
        });
    }
    
}
```

# Registering Flags
To register flags, annotate the command method with `@CommandFlags(Flag[] value)`. Then, you pass in a list
that has all flag annotations and details to link them to the command.  

Then, to access the flags, add the `Flags` parameter to the function parameters.

## Flag Definitions
For each individual `@Flag` annotation, you can choose to define these flags with the following fields...
* `flag` - short flag definition (`/command -flag`)
* `longFlag` - long flag definition (`/command --longFlag`)
* `argument` - java class of the type of argument desired
* `suggestion` - string suggestion argument




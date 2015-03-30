# Introduction #

You can add UML diagrams in your AsciiDoc document using `[plantuml]` block.
PlantUML uses `@startuml/@enduml` lines, these lines will be automatically appended so you don't need to use them, but you can if you like to or if you copy your PlantUML code from somewhere else.

Filter available in download page contains it's own copy of PlantUML.jar. If you want to use your own PlantUML, please replace one in the zip file.

# parameters #
Following parameters are available:
```
["plantuml", target, format]
```

  * `target` - optional, output file
  * `format` - optional, output format: png(default), svg, eps

# Examples #

### Use case diagram ###
```
["plantuml"]
---------------------------------------------------------------------
User -> (Start)
User --> (Use the application) : Polish label-Zażółć gęślą jaźń

:Main Admin: ---> (Use the application) : This is\nyet another\nlabel
---------------------------------------------------------------------
```
![http://asciidoc-plantuml.googlecode.com/git/IMG/use.png](http://asciidoc-plantuml.googlecode.com/git/IMG/use.png)

### Sequence diagram ###
```
["plantuml", "sequence.png"]
---------------------------------------------------------------------
participant User

User -> A: DoWork
activate A #FFBBBB

A -> A: Internal call
activate A #DarkSalmon

A -> B: << createRequest >>
activate B

B --> A: RequestCreated
deactivate B
deactivate A
A -> User: Done
deactivate A
---------------------------------------------------------------------
```
![http://asciidoc-plantuml.googlecode.com/git/IMG/sequence.png](http://asciidoc-plantuml.googlecode.com/git/IMG/sequence.png)

### State diagram ###
```
["plantuml", "state.png", "png"]
---------------------------------------------------------------------
[*] --> NotShooting

state NotShooting {
  [*] --> Idle
  Idle --> Configuring : EvConfig
  Configuring --> Idle : EvConfig
}

state Configuring {
  [*] --> NewValueSelection
  NewValueSelection --> NewValuePreview : EvNewValue
  NewValuePreview --> NewValueSelection : EvNewValueRejected
  NewValuePreview --> NewValueSelection : EvNewValueSaved
  
  state NewValuePreview {
     State1 -> State2
  }
  
}
---------------------------------------------------------------------
```
![http://asciidoc-plantuml.googlecode.com/git/IMG/state.png](http://asciidoc-plantuml.googlecode.com/git/IMG/state.png)

### Activity diagram ###
```
["plantuml", "activity.svg", "svg"]
---------------------------------------------------------------------
(*)  --> "check input"
If "input is verbose" then
--> [Yes] "turn on verbosity"
--> "run command"
else
--> "run command"
Endif
-->(*)
---------------------------------------------------------------------
```
![http://asciidoc-plantuml.googlecode.com/git/IMG/activity.png](http://asciidoc-plantuml.googlecode.com/git/IMG/activity.png)

### Class diagram ###
```
["plantuml", "activity.png", "png"]
---------------------------------------------------------------------
class Object << general >>
Object <|--- ArrayList

note top of Object : In java, every class\nextends this one.

note "This is a floating note" as N1
note "This note is connected\nto several objects." as N2
Object .. N2
N2 .. ArrayList
---------------------------------------------------------------------
```
![http://asciidoc-plantuml.googlecode.com/git/IMG/class.png](http://asciidoc-plantuml.googlecode.com/git/IMG/class.png)

# More #
For more examples look at PlantUML page: http://plantuml.sourceforge.net/screenshot.html .
### Comments are comprehensible and add something to the maintainability of the code

Yes

### Comments are neithertoo numeroues nor verbose

Yes, but still sometimes some bad inline comments: 

```java
// Write choiceboxes.
writeChoiceBoxes();
// Write filters.
writeFilters();
// Write xaxis.
writeXaxis();
// Write series.
writeSeries();
```

### Types have been generalized where possible

Yes (GUI)

### Parameterized Types have been used appropriately

kP

### Exceptions have been used appropiately

No: Stacktrace will just be printed to the console (no user can see it) and code execution isn't even stopped.

```java
try {
  System.out.println("connecting");
  tmp = (RmiInterface) Naming
      .lookup("rmi://" + "10.179.9.188" + ":" + Registry.REGISTRY_PORT + "/RMIInterface");
  System.out.println("Connected");
} catch (NotBoundException e) {
  e.printStackTrace();
} catch (MalformedURLException e) {
  e.printStackTrace();
} catch (RemoteException e) {
  e.printStackTrace();
}
 ```
 
### Repetitive Code has been factored out

GUI: Yes
Crawler: some duplicate code Airline7CityLookupService

### Frameworks have been used appropriately

GUI: Yes, but layout is pixel fixed (zero responsiveness)
Crawler: No framework

### Command classes have been used appropriately - methods have all been defined appropriately

Yes

### Command classes have been designed to undertake one task only

Yes, but SettingsSerializer is very complex.

### Unit tests are present and correct

No (GUI)
Crawler: 1 Test present

### Common errors have been checked for

GUI: No
Crawler: Some Declariation Redundancy present

### Potential threading issues have been eliminated where possible

GUI: Yes (no multithreading)
Crawler: Yes, see above

### Any security concerns have been adressed

RMI allows unauthenticated network attacks that can result in operating system takeover including arbitrary code execution

No security Manageris set

Crawler: Not necessary

### Performance was considered

Crawler: not measurable

### The functionality fits the current design, architecture

GUI: Yes
Crawler:n Yes

### The code is unit testable

GUI: partially
Crawler: small part

### The code does not use unjustifiable static methods/blocks

GUI:Yes
Crawler: Yes

### The code complies to coding standards

Crawler: Yes

### Logging used appropriately

GUI: No, bad souts
Crawler: Logger used

### Possibility of NPE



### Are requirements marked as `done` in specification document really completed?

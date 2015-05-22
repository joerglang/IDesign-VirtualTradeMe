# IDesign-VirtualTradeMe
This is a sample solution showing the project layout of a Method based design. 
This sample helps in understanding namespace and folder structure guidelines as proposed by IDesign. I tried to base that sample on the *VirtualTradeMe* sample that many of the IDesign alumni know. The sample is not a working application but just a skeleton. (Maybe that skeleton can be filled with actual, fleshed out service contracts and data contracts...) 

The solution was created to digest the input and guidelines from the IDesign Alumni thread called **Namespace convention and namespace best practices**.
The Visual Studio solution presented here has been *validated* by Monty (Michael Montgomery) from IDesign. However he did not validate 
against the *VirtualTradeMe* sample. 

## Namespace convention and namespace best practices 
In the following I try to consolidate the most important aspects of that IDesign Alumni thread.

### Basic guideline
Basic guideline for namespaces is 

`<Company>.<Concept>.[<Product>].<Subsystem>`

* Company part is clear. 
* Concept can be one of `Contract, DataAccess, Engine, Manager, Proxy, Test`
* The optional Product part is used for code that targets a specific "client product". 
The Product designation originated from the ISV space where for example the **Mobile** version was a separate ‘product context’ with
separate licensing, pricing, etc. If your domain is not an ISV, the Product part might not be used. 
* The subsystem depends on the architecture. Given the VirtualTradeMe sample I have come up with `Education, Market, Membership and Notification` 
as the subsytems. Parts of the code that cannot be assigned to one of those subsystems should use `Common` as the 
subsystem designation.

### Exceptions
But because we have "standard" reusable services that will be used in all Method based designs, there are exceptions to the above. Namely we have 
* Utilities
* iFX (Infrastucture)

#### Utilities
Most likeley we have utilities for Auditing, Logging, ServiceBus, Metrics and so on. Each of these utilities conists of several parts (projects) that use the same concepts used in the basic guideline. So for example the Logging utility
has seperate projects for `Contract, DataAccess, Manager, Proxy and Test`. Logging probably does not have an `Engine`
but maybe another utility might. Also note that the tests for the utility is kept seperate from the "domain" tests.

So the naming convention here is `<Company>.Utilities.<Utility>.<Concept>`

#### iFX or Infrastructure
Is same as utilities in regards to naming conventions. iFX contains code to make your life easier. For example don't create a seperate host for each of your managers, but have a `Host` project in iFX that uses conventions to automatically pick up all managers and creates hosts for them.

So the naming convention here is `<Company>.iFX.<Concept>`

## Folder structure
The folder structure you use is the same as the namespace. On each dot in the namespace you create a folder in Explorer.

## Solution folders
Use solutions folder inside Visual Studio to structure your project. This helps you to keep overview over the many projects a Method basid design will create.

## Contracts
Only the public contracts of the managers are kept in the projects under the `<Concept>` of `Contracts`. The interfaces of Engines and DataAccess are kept within their respective solutions because they don't need to be public. Usually Engines and DataAccess are instantiated InProc and it does not really hurt when the Manager needs a reference to the Engines or DataAccess project(s).









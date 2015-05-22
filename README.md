# IDesign-VirtualTradeMe
A sample solution showing the project layout of a Method based design. 
This sample helps in understanding namespace and folder structure guidelines as propesed by IDesign. I tried to base that sample 
on the *VirtualTradeMe* sample that many of the IDesign alumni know. The sample is not a working application but just a skeleton. 

The solution was created to digest the input and guidelines from the IDesign Alumni thread called **Namespace convention and namespace best practices**.
The Visual Studio solution presented here has been *validated* by Monty (Michael Montgomery) from IDesign. However he did not validate 
against the *VirtualTradeMe* sample. 

## Namespace convention and namespace best practices 
In the following I try to consolidate the most important aspects of that thread.

### Basic guideline
Basic guideline for namespaces is 

`<Company>.<Concept>.[<Product>].<Subsystem>`

* Company part is clear. 
* Concept can be one of `Contract, DataAccess, Engine, Manager, Proxy`
* The optional Product part is used for code that targets a specific "client product". 
The Product designation originated from the ISV space where for example the **Mobile** version was a separate ‘product context’ with
separate licensing, pricing, etc. If your domain is not an ISV, the Product part might not be used. 
* The subsystem depends on the architecture. Given the VirtualTradeMe sample I have come up with `Education, Market, Membership and Notification` 
as the subsytems. Parts of the code that cannot be assigned to one of those subsystems should use `Common` as the 
subsystem designation.

### Exceptions
But because we have "standard" reusable services that will be used in all Method based designs, there are exceptions to the above 




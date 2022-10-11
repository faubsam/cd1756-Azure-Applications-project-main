# Write-up Template

### Analyze, choose, and justify the appropriate resource option for deploying the app.

*For **both** a VM or App Service solution for the CMS app:*
- *Analyze costs, scalability, availability, and workflow*
- *Choose the appropriate solution (VM or App Service) for deploying the app*
- *Justify your choice*

APP SERVICE CONSIDERATIONS
- cost
    Since the app would likely be running all the time, the cost for app service would probably be lower than the VM. The VM would be more cost-efficient if the app was only run 
    on a timetable and the service could be stopped, thus savings on operational costs - but this is not the case.
- scalability
    App service is less scalable than VM with scale sets, but this app is a simple CMS app that probably will not grow exponentially in the near future. App service should be 
    be able to handle the memory and performance scaling requirements.
- availability
    High availability is built-in to app service. 
- workflow
    App service supports python runtime environments and easily integrates with Azure DevOps and github. Making changes to the app and deploying them would be fairly easy.

VM CONSIDERATIONS
- cost
    Since this is a web app, the VM would likely be running on a continuous basis. This would likely make it more expensive than using app service, and would also incur additional
    labour costs to maintain the VM operating systems, dependencies and security. 
- scalability
    Using VM scale sets would provide a very robust scalable option for the app. However, given the application's profile, this is unlikely to be required for a while.
- availability
    Scale sets and load balancers across more than 1 region would provide high availability for the app, but requires more configuration than using app service's built-in features.
- workflow
    VM would have to be mnually updated. The integration with DevOps would also have to be configured.


Based on the current analysis, using App Service is the better choice to deploy this app. App Service provides a scalable and highly available solution at a similar or lower cost than VM, while also providing easy integration with DevOps. Using VM would incur additional costs, configurations and maintenance that would not be required at this time. 


### Assess app changes that would change your decision.

*Detail how the app and any other needs would have to change for you to change your decision in the last section.* 

The main consideration that would change the needs of the application would be related to scaling and resource constraints. If the app grew to a point where it reaches the limits of the physical resources allowed by App service (14Gb of memory and 4 vCPUs), then switching to more powerful virtual machines would become an option. Another possibility is if the app was ever re-written in a language that is not supported by App Service, such as Go. 
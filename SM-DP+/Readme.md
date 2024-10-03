# Subscription Manager Data Preparation +

The SM-DP+ is responsible for the creation, generation, management and the protection of resulting Profiles upon the input/request of the Operator on behalf of served Mobile Service Providers.  
It is also responsible for the delivery of a Profile within a Bound Profile Package, making the Bound Profile Package available for the secure delivery.  
In addition, the SM-DP+ is responsible for requesting the creation of the ISD-P in the eUICC into which the Profile will be installed.  
The SM-DP+ will also be the off-card entity that will be responsible for the lifecycle management of the ISD-P that was created at its request.

## Functions:

### Profile Package Generation
Creates Profile Packages (i.e. Personalised Profiles, including (IMSI, Ki, ICCID,…)) from Profile Descriptions agreed with Operators. This can be an off-line batch or real time process.

### Profile Package Protection
Secures each Profile Package according to the security process creating the Protected Profile Package.

### Profile Package Binding
Binds the Protected Profile Package to a target eUICC using the security process thus creating the Bound Profile Package.

### Profile Package Storage
Temporarily stores Protected Profile Packages or Bound Profile Packages for subsequent delivery to the eUICC.

### Profile Package Delivery
Securely transmits and installs the Bound Profile Package to the eUICC through the LPA.

### SM-DS Event
Registration Notifies the SM-DS of a pending operation for a specific eUICC.

### Remote Profile Management
Profile Management operations (Enabling, Disabling, deleting, list Profile information, query, update Metadata) within the eUICC managed by the
Managing SM-DP+. RPM command authorisation is enforced by the eUICC.

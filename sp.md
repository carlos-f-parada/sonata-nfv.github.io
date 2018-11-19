# Service Platform

With the installation of the Service Platform ready and the Descriptors already created is time to deploy our network service. To this end, you will need to fulfill a set of prerequisited described below.

## Platform Channels

### Portal

Write the url (ip) of your service platform in any browser and you will be redirected to GUI's main dashboard:

<p align="center"><img src="images/dashboard.jpg" /></p>


In the SP you can configure the Services, the Functions and the Network Slices


Here is where you can work with your Network Services. You can deploy, check the status and terminate them:

<p align="center"><img src="images/sm.jpg" /></p>

### APIs

## Platform SETUP

### Configure VIMs/WIMs

   After the installation of the SP, you need to attach a VIM. You can use [this](https://raw.githubusercontent.com/sonata-nfv/sonata-nfv.github.io/master/vim_script.sh) bash script to perform this task. To customize the configuration you will need to edit the script and modify the variables.

```bash
#!/bin/bash
user="username"
password="password"
tenant="tenantname"
vim_ip="000.000.000.000"
router="tenant router uuid"
ext_net="external net uuid"
city="city"
country="country"
name="vimname"
```

To get the tenant router uuid you can go to openstack horizon dashboard and open the route: `project -> network -> routers -> (select your router) -> Overview -> ID`

<p align="center"><img src="images/router-uuid.png" width="70%" /></p>


### Upload Images

VNF images available in Openstack:
   
Check that the images are available in openstack if not you can upload these two images:
   a. [squid](http://bit.ly/5GTANGO_squid)
   b. [haproxy](http://bit.ly/5GTANGO_HAproxy)


## Platform Operation

This section shows the basic operation using the SONATA Service Platform (SP).

### Catalogue Artifacts

The SP considers multiple artifacts, which are stored in the Catalogue and can be used to instanciate services.
- **Packages**, a zipped file, which typically contains the descriptors of a service (NSD) and respective VNFs (VNFDs). It can include the VNF software images (fat package) or just a link where the software images can be downloaded (slim package).
- **Services**, a full ETSI NFV network service (NS), which represent a service provided to a user, and composed by multiple VNFs interconnected among VLs and CPs, and which can beoptionally chained through a VNF forwading graph (VNGFG).
- **Functions**, ETSI NFV virtual network functions (VNF), which implements a virtualized version of a traditional network function, and can be composed by multiple components (VNFCs).
- **Components**, ETSI VNF components (VNFCs), which implement a sub-function of the VNF, and usually implemented by a unitary workload, e.g. a Virtual Machine (VM).

#### Packages

Network service descriptor on-boarded to the Service Platform
   Check if the Package is available in the service plaform. It can be done with the command: `curl http://<service_platform_ip>/api/v3/packages`. If the Network Service is not avaible then you can on-board using this command: `curl -X POST http://<service_platform_ip>/api/v3/packages -F "package=@./eu.5gtango.ns-squid-haproxy.0.1.tgo" -H 'content-type:multipart/form-data`. The package is availabe in [here](files/eu.5gtango.ns-squid-haproxy.0.1.tgo)
   
#### Services
#### Functions
### Instantiate a Service

Login and verify that the selected section is “Available Network Services” inside the Service Management. Here you can see the green play button. After pressing it the instantiation process will begin.

<p align="center"><img src="images/instantiate.jpg" /></p>


### Show Service Instance

In the Dashboard, in the Network Service tab, you can check the status of the instantiated services.

<p align="center"><img src="images/sp.jpg" /></p>

### Terminate a Service Instance

In the section is “Network Services Instances” inside the Service Management. Here you can see the red stop button. After pressing it the terminate process will begin.

<p align="center"><img src="images/terminate.jpg" /></p>

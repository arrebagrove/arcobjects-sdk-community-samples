##Find near features SOAP SOE

###Purpose  
This sample illustrates the basic framework for creating a server object extension (SOE) that will be accessed as an ArcGIS Server SOAP SOE. The SOE extends the functionality of a map service with a basic geospatial operation—namely the ability to find features in all feature layers via a user-defined location and distance.  This sample is divided into the following parts: The SOE implementation, which receives SOAP messages, processes requests, and generates SOAP responses.  A simple desktop client to consume the custom SOE via SOAP.  All the information needed to deploy the SOE is included in this sample encapsulated in a .soe file. Deploying the SOE from this file does not require you to open Visual Studio. However, you can open the Visual Studio solution included with this sample to explore the coding patterns used in the SOE. The instructions in this topic assume that you have installed the developer kit on the machine running ArcGIS Server Manager. If you have installed the developer kit on another machine, you need to copy the .soe file to the machine running Manager, or make the .soe file visible to Manager by placing it in a shared folder.  


###Usage
####Deploy the SOE  
1. Log in to ArcGIS Server Manager and click Site.  
1. Click Extensions.  
1. Click Add Extension.  
1. Click Browse and navigate to the .soe file, which by default is located at <ArcGIS DeveloperKit install location>\Samples\ArcObjectsNet\ServerFindNearSOAPSOE\CSharp\FindNearFeaturesSoapSOE\bin\Debug\FindNearFeaturesSoapSOE.soe.   
1. Click OK.  

####Enable the SOE on a service  
1. Start ArcMap and click File > Open.  
1. Browse to or type the location of USA.mxd, which is located in <ArcGIS Developer Kit Location>\Samples\data\Usa.  
1. Click File > Share As > Service.  
1. Click "Save a service definition" and click Next.  
1. Choose "No available connection" and select "Include data in service definition when publishing."  
1. Change the Server type to ArcGIS Server.  
1. Leave the Service name as USA and click Next.  
1. Choose a location where you want to save the service definition, then click Continue.  
1. Click Stage to create the service definition. In the success message, note the path of your service definition (.sd) file.  
1. Copy the USA.sd file to the machine running ArcGIS Server Manager.  
1. On the machine running ArcGIS Server Manager, log in to Manager and click Services.  
1. If necessary, click the Manage Services tab.  
1. Click Publish Service.  
1. Click Browse. Browse to the location of USA.sd on the local machine, click Open, then click Next.  
1. Accept the default properties for the service by clicking Next.  
1. Click Publish. This creates the USA map service.  
1. On the Services tab of Manager, select the USA map service, then select Capabilities. In the list of available capabilities, find ".NET Find Near Features SOAP SOE" and select the check box to enable it. If there is a list of available operations allowed, select all of them.  
1. Click the Save and Restart button to restart the service.  

####Use the SOE in a client application  
1. In Visual Studio, open the FindNearFeaturesSoapClient<vs_version> solution (for example, FindNearFeaturesSoapClient2010.sln). The <vs_version> references the Visual Studio version of the solution. The application contains a simple Windows form with a button and a text box.   
1. A Web Reference has been added to the project to reference the SOE SOAP endpoint hosted within the ArcGIS Server Web service instance. Open the code behind for Form1 (Form1.cs).   
1. In the click event for the button, change the URL property of the proxy instance to reference the HTTP URL to the map service created in the previous section, then append the path to the FindNearFeaturesSOAPSOE (for example: http://<server name>:6080/arcgis/services/USA/MapServer/FindNearFeaturesSoapSOE), where USA is the map service name on which the Find Near Features SOE has been enabled.   
1. Run the application and click Execute. Layer information for all layers and features near the center of the default map extent for the service will be returned. All returned content displays in the rich text box in the form.   









---------------------------------

####Licensing  
| Development licensing | Deployment licensing | 
| :------------- | :------------- | 
|  |  |  



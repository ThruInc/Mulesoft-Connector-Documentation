# Thru MFT Connector Demo
#
Demo flow description
------------
**mule-thru-mft-connector-crud-operation-demoFlow**  : This sample Mule flow demonstrates the usage of four operations of the Thru MFT connector:
- On File Pickup Source
- File Dropoff
- File Metadata
- Flow Outcome

On execution of the flow, the connector will execute the "On File Pickup Source" operation to determine if any files are available to be retrieved from the "Source" transport. If a file is ready, the file will be transferred into the flow.

The file will then be delivered to the "Target" transport on Thru's servers using the "File Dropoff" operation.  An example DataWeave is performed on the output to convert the generic 'fileCode' to a dropoff specific type.

The "File Metadata" operation is then performed to get any metadata associated with the file that was just picked up from the Thru "Source" transport.  Another DataWeave operation is performed on the returned metadata to add additional processing information and demonstrate basic DataWeave tranformation.

The "Flow Outcome" operation is then executed.  This operation informs the "Source" transport on Thru's servers with the Mule flow's processing results. 

**mule-thru-mft-connector-pickup-operation-demoFlow**  : This sample Mule flow demonstrates the usage of File Pickup mid flow

On execution of the flow, the Scheduler will execute the "File Pickup" operation every 7 seconds to determine if any files are available to be retrieved from the Thru transport configured in the 'mule-thru-demo.properties' file. If a file is ready, the file will be transferred into the flow.

The "Flow Outcome" operation is then executed.  This operation informs the "Source" transport on Thru's servers with the Mule flow's processing results. 

Note: A Participant (Partner) subscribed to a Thru MFT Transport (MFT workflow) uploads a file to an FTP location.  The Thru Transport fetches the file from the location and makes it available for Mule flows via the connectors "On File Pickup Source" operation. 
Thru MFT connector operations used in this Mule flow: File Pickup, File Dropoff, Flow Outcome.

HOW TO RUN THE DEMO
---------------

### Prerequisites
In order to build and run this demo project you need:

* Anypoint Studio with Mule Runtime 4.0.0 EE or higher
* Mule Thru MFT Connector (from Mulesoft Exchange)
* An account in Thru MFT development environment or an instance of Thru MFT server deployed in Thru Sandbox or on premise with your organization.
* Thru demo transports which support Mule demo flows listed here.

### Test the flows

* Import the demo project into your workspace:
	* Go to **File > Import**
	* Select **Anypoint Studio Project from File System** (under the parent folder "Anypoint Studio")
	* Provide the root path to the demo project folder.  From a cloned ThruInc/Mulesoft-Connector-Documentation repository, the path is './Mulesoft-Connector-Documentation/demo/'
	* Select Mule Runtime (4.x.x EE).
	* Click **Finish**.

* Run the Mule Project.

### Configuration Note
* Test flows are pre-configured to run with Thru's sandbox environment.  The configuration should be edited to work with other environments such as Thru MFT development environment or an instance of Thru MFT server deployed on premise with your organization.
* The connector configuration is read from src/main/resources/mule-thru-demo.properties.  Modify this file as needed.
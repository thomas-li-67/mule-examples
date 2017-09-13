# SAP FI data retrieval Example

This example application illustrates how to use Mule ESB to build a simple HTTP application using APIKit to fetch data from SAP. 


### Assumptions

- A working knowledge of the SAP business context and in particular, the SAP R/3 Business Suite.
- A basic understanding of the SAP NetWeaver Platform from an administration point of view.
- Some fundamental knowledge of the ABAP language.
- SAP JCO which your download from SAP.



### Example Use Case

This application employs APIKit Router component to route HTTP requests to exact flow defined by resource and method. Afterwards, the flows prepare XML request for SAP connector using the HTTP input parameters. The response is transformed to the JSON and returned to the user.

### Set Up and Run the Example

You can create the applications straight out of the box in Anypoint Studio. You can tweak the configurations of these use case-based examples to create your own customized applications in Mule.

Follow the procedure below to create, then run the **SAP FI data retrieval** application.

1. Clone the git repository from [github](https://github.com/thomas-li-67/mule-examples) and open the sap-fi-data-retrieval-v1.0 project in Anypoint Studio from [Anypoint Exchange](http://www.mulesoft.org/documentation/display/current/Anypoint+Exchange).
2. In your application in Studio, click the **Global Elements** tab. Double-click the HTTP Listener global element to open its **Global Element Properties** panel. Change the contents of the **port** field to required HTTP port e.g. 8081
3. Go to Global Elements and open SAP Connector element. Fill in your SAP credentials.
4. Run the application.
The APIKit console should start and the user can choose which endpoint wants to hit. The main
	+	GET /accounts 	- return chart of accounts from SAP instance according the specified parameters
						- user are able to define 1 HTTP query parameters - company_code
		+ company_code - defining company code	

5. Click on the resource which yhou want to use, specify the parameters and click on *GET* button.
6. You will see the retrieved data structure. If the data in SAP instance does not match your criteria, "No data found" message is returned,

### How it Works

The **SAP FI data retrieval** example application contains two flows. The main flow receive user HTTP requests and using the APIKit routing to the right flow.


### get:/accounts:sap-api-config

This flow is responsible for displaying chart of accounts used in the general ledger of an organization from SAP system. 
At the beginning, using the [DataWeave transformer](https://docs.mulesoft.com/mule-user-guide/v/3.8/dataweave)the XML request from the HTTP input parameters is prepared. 
Next, the [SAP connector](https://docs.mulesoft.com/mule-user-guide/v/3.8/sap-connector) is used to retrieve the data using the BAPI - BAPI_GL_ACC_GETLIST. 
Finally, the response from SAP is transformed by DataWeave transformer into JSON structure and sent back to HTTP. 



### Next

- Learn more about the [HTTP endpoint](http://www.mulesoft.org/documentation/display/current/HTTP+Connector).
- Learn more about the [SAP connector](https://docs.mulesoft.com/mule-user-guide/v/3.8/sap-connector)
- Learn more about the [APIKit router](https://docs.mulesoft.com/anypoint-platform-for-apis/apikit-tutorial)

# SAP UI5 Demo Remote OData Service

A Remote OData service refers to an OData (Open Data Protocol) service that is hosted and accessible over a network, typically the internet. OData is a standard protocol for building and consuming RESTful APIs, and it enables the creation and consumption of RESTful web services that allow resources, identified using URLs and defined in a data model, to be published and edited by web clients using simple HTTP protocols.

#### Note 
This demo created using VS Code.

### Code explaination

Refer to [/ui5.yaml](https://github.com/VaibhavMojidra/SAP-UI5---Demo-Remote-OData-Service/blob/master/ui5.yaml "ui5.yaml")

In this demo, we want to use the publicly available Northwind OData service located at https://services.odata.org/V2/Northwind/Northwind.svc/. Therefore, our URI points to the official Northwind OData service. In order to avoid cross-origin resource sharing, the typical procedure is to use a proxy in UI5 Tooling and maintain only a path in the URI property of the data source of our app.
we'll use ui5-middleware-simpleproxyInformation published on non SAP site. Open a new terminal window in your app root folder and execute npm i -D ui5-middleware-simpleproxy to install this package as a new development dependency in your package.json.
Configure our proxy in the ui5.yaml file. The mountPath property configures which URLs will be caught by the proxy. The configuration/baseUri property stores the real server address.


Refer to [/webapp/manifest.json](https://github.com/VaibhavMojidra/SAP-UI5---Demo-Remote-OData-Service/blob/master/webapp/manifest.json "manifest.json")

In the sap.app section of the descriptor file, we add a data source configuration. With the invoiceRemote key, we specify a configuration object that allows automatic model instantiation. We specify the type of the service (OData) and the model version (2.0).

In the models section, we replace the content of the invoice model. This key is still used as model name when the model is automatically instantiated during the component initialization. However, the invoiceRemote value of the dataSource key is a reference to the data source section that we specified above. This configuration allows the component to retrieve the technical information for this model during the start-up of the app.

Our component now automatically creates an instance of sap.ui.model.odata.v2.ODataModel according to the settings we specified above, and makes it available as a model named invoice. When you use the invoiceRemote data source, the ODataModel fetches the data from the real Northwind OData service.

---

[![Vaibhav Mojidra - 1.jpeg](https://raw.githubusercontent.com/VaibhavMojidra/SAP-UI5---Demo-Remote-OData-Service/master/screenshot/1.jpeg "Vaibhav Mojidra")](https://vaibhavmojidra.github.io/site/)
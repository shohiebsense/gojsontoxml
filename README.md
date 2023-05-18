# gojsontoxml

conversion from `map[string]interface{}` a.k.a `any` to (hopefully) a valid xml in `[]byte`.

## usage example

```.go
dataBytes, err := gojsontoxml.JsonToXml(data)

if err != nil {
   log.Panicln(err)
   return
}
  
w.Header().Set("Content-Type", "application/xml")
w.Write(dataBytes)
	
```

Todo: test cases 

Complains, feedbacks, opinions are appreciated.  

### tests

```.json
{"web-app": {
  "servlet": [   
    {
      "servlet-name": "cofaxCDS",
      "servlet-class": "org.cofax.cds.CDSServlet",
      "init-param": {
        "configGlossary:installationAt": "Philadelphia, PA",
        "configGlossary:adminEmail": "ksm@pobox.com",
        "configGlossary:poweredBy": "Cofax",
        "configGlossary:poweredByIcon": "/images/cofax.gif",
        "configGlossary:staticPath": "/content/static",
        "templateProcessorClass": "org.cofax.WysiwygTemplate",
        "templateLoaderClass": "org.cofax.FilesTemplateLoader",
        "templatePath": "templates",
        "templateOverridePath": "",
        "defaultListTemplate": "listTemplate.htm",
        "defaultFileTemplate": "articleTemplate.htm",
        "useJSP": false,
        "jspListTemplate": "listTemplate.jsp",
        "jspFileTemplate": "articleTemplate.jsp",
        "cachePackageTagsTrack": 200,
        "cachePackageTagsStore": 200,
        "cachePackageTagsRefresh": 60,
        "cacheTemplatesTrack": 100,
        "cacheTemplatesStore": 50,
        "cacheTemplatesRefresh": 15,
        "cachePagesTrack": 200,
        "cachePagesStore": 100,
        "cachePagesRefresh": 10,
        "cachePagesDirtyRead": 10,
        "searchEngineListTemplate": "forSearchEnginesList.htm",
        "searchEngineFileTemplate": "forSearchEngines.htm",
        "searchEngineRobotsDb": "WEB-INF/robots.db",
        "useDataStore": true,
        "dataStoreClass": "org.cofax.SqlDataStore",
        "redirectionClass": "org.cofax.SqlRedirection",
        "dataStoreName": "cofax",
        "dataStoreDriver": "com.microsoft.jdbc.sqlserver.SQLServerDriver",
        "dataStoreUrl": "jdbc:microsoft:sqlserver://LOCALHOST:1433;DatabaseName=goon",
        "dataStoreUser": "sa",
        "dataStorePassword": "dataStoreTestQuery",
        "dataStoreTestQuery": "SET NOCOUNT ON;select test='test';",
        "dataStoreLogFile": "/usr/local/tomcat/logs/datastore.log",
        "dataStoreInitConns": 10,
        "dataStoreMaxConns": 100,
        "dataStoreConnUsageLimit": 100,
        "dataStoreLogLevel": "debug",
        "maxUrlLength": 500}},
    {
      "servlet-name": "cofaxEmail",
      "servlet-class": "org.cofax.cds.EmailServlet",
      "init-param": {
      "mailHost": "mail1",
      "mailHostOverride": "mail2"}},
    {
      "servlet-name": "cofaxAdmin",
      "servlet-class": "org.cofax.cds.AdminServlet"},
 
    {
      "servlet-name": "fileServlet",
      "servlet-class": "org.cofax.cds.FileServlet"},
    {
      "servlet-name": "cofaxTools",
      "servlet-class": "org.cofax.cms.CofaxToolsServlet",
      "init-param": {
        "templatePath": "toolstemplates/",
        "log": 1,
        "logLocation": "/usr/local/tomcat/logs/CofaxTools.log",
        "logMaxSize": "",
        "dataLog": 1,
        "dataLogLocation": "/usr/local/tomcat/logs/dataLog.log",
        "dataLogMaxSize": "",
        "removePageCache": "/content/admin/remove?cache=pages&id=",
        "removeTemplateCache": "/content/admin/remove?cache=templates&id=",
        "fileTransferFolder": "/usr/local/tomcat/webapps/content/fileTransferFolder",
        "lookInContext": 1,
        "adminGroupID": 4,
        "betaServer": true}}],
  "servlet-mapping": {
    "cofaxCDS": "/",
    "cofaxEmail": "/cofaxutil/aemail/*",
    "cofaxAdmin": "/admin/*",
    "fileServlet": "/static/*",
    "cofaxTools": "/tools/*"},
 
  "taglib": {
    "taglib-uri": "cofax.tld",
    "taglib-location": "/WEB-INF/tlds/cofax.tld"}}}
```  


Result:  
```.xml
<?xml version="1.0" encoding="UTF-8"?>
<Object>
	<web-app>
		<servlet>
			<servlet>
				<servlet-name>cofaxCDS</servlet-name>
				<servlet-class>org.cofax.cds.CDSServlet</servlet-class>
				<init-param>
					<searchEngineRobotsDb>WEB-INF/robots.db</searchEngineRobotsDb>
					<useDataStore>true</useDataStore>
					<configGlossarypoweredBy>Cofax</configGlossarypoweredBy>
					<configGlossarypoweredByIcon>/images/cofax.gif</configGlossarypoweredByIcon>
					<dataStoreTestQuery>SET NOCOUNT ON;select test=&apos;test&apos;;</dataStoreTestQuery>
					<dataStoreInitConns>10.000000</dataStoreInitConns>
					<dataStoreLogLevel>debug</dataStoreLogLevel>
					<maxUrlLength>500.000000</maxUrlLength>
					<cachePackageTagsTrack>200.000000</cachePackageTagsTrack>
					<dataStoreName>cofax</dataStoreName>
					<cacheTemplatesRefresh>15.000000</cacheTemplatesRefresh>
					<redirectionClass>org.cofax.SqlRedirection</redirectionClass>
					<jspListTemplate>listTemplate.jsp</jspListTemplate>
					<cachePackageTagsRefresh>60.000000</cachePackageTagsRefresh>
					<cachePagesDirtyRead>10.000000</cachePagesDirtyRead>
					<templatePath>templates</templatePath>
					<cachePagesRefresh>10.000000</cachePagesRefresh>
					<cachePagesStore>100.000000</cachePagesStore>
					<searchEngineListTemplate>forSearchEnginesList.htm</searchEngineListTemplate>
					<dataStoreUser>sa</dataStoreUser>
					<configGlossaryinstallationAt>Philadelphia, PA</configGlossaryinstallationAt>
					<defaultFileTemplate>articleTemplate.htm</defaultFileTemplate>
					<jspFileTemplate>articleTemplate.jsp</jspFileTemplate>
					<dataStoreUrl>jdbc:microsoft:sqlserver://LOCALHOST:1433;DatabaseName=goon</dataStoreUrl>
					<dataStoreLogFile>/usr/local/tomcat/logs/datastore.log</dataStoreLogFile>
					<dataStoreMaxConns>100.000000</dataStoreMaxConns>
					<configGlossarystaticPath>/content/static</configGlossarystaticPath>
					<templateProcessorClass>org.cofax.WysiwygTemplate</templateProcessorClass>
					<defaultListTemplate>listTemplate.htm</defaultListTemplate>
					<cachePackageTagsStore>200.000000</cachePackageTagsStore>
					<cacheTemplatesTrack>100.000000</cacheTemplatesTrack>
					<cacheTemplatesStore>50.000000</cacheTemplatesStore>
					<cachePagesTrack>200.000000</cachePagesTrack>
					<searchEngineFileTemplate>forSearchEngines.htm</searchEngineFileTemplate>
					<configGlossaryadminEmail>ksm@pobox.com</configGlossaryadminEmail>
					<templateLoaderClass>org.cofax.FilesTemplateLoader</templateLoaderClass>
					<dataStoreConnUsageLimit>100.000000</dataStoreConnUsageLimit>
					<dataStoreClass>org.cofax.SqlDataStore</dataStoreClass>
					<dataStorePassword>dataStoreTestQuery</dataStorePassword>
					<dataStoreDriver>com.microsoft.jdbc.sqlserver.SQLServerDriver</dataStoreDriver>
					<templateOverridePath/>
					<useJSP>false</useJSP>
				</init-param>
			</servlet>
			<servlet>
				<servlet-name>cofaxEmail</servlet-name>
				<servlet-class>org.cofax.cds.EmailServlet</servlet-class>
				<init-param>
					<mailHost>mail1</mailHost>
					<mailHostOverride>mail2</mailHostOverride>
				</init-param>
			</servlet>
			<servlet>
				<servlet-name>cofaxAdmin</servlet-name>
				<servlet-class>org.cofax.cds.AdminServlet</servlet-class>
			</servlet>
			<servlet>
				<servlet-class>org.cofax.cds.FileServlet</servlet-class>
				<servlet-name>fileServlet</servlet-name>
			</servlet>
			<servlet>
				<servlet-name>cofaxTools</servlet-name>
				<servlet-class>org.cofax.cms.CofaxToolsServlet</servlet-class>
				<init-param>
					<log>1.000000</log>
					<dataLogMaxSize/>
					<removePageCache>/content/admin/remove?cache=pages&amp;id=</removePageCache>
					<removeTemplateCache>/content/admin/remove?cache=templates&amp;id=</removeTemplateCache>
					<fileTransferFolder>/usr/local/tomcat/webapps/content/fileTransferFolder</fileTransferFolder>
					<betaServer>true</betaServer>
					<templatePath>toolstemplates/</templatePath>
					<logLocation>/usr/local/tomcat/logs/CofaxTools.log</logLocation>
					<logMaxSize/>
					<dataLog>1.000000</dataLog>
					<dataLogLocation>/usr/local/tomcat/logs/dataLog.log</dataLogLocation>
					<lookInContext>1.000000</lookInContext>
					<adminGroupID>4.000000</adminGroupID>
				</init-param>
			</servlet>
		</servlet>
		<servlet-mapping>
			<cofaxCDS>/</cofaxCDS>
			<cofaxEmail>/cofaxutil/aemail/*</cofaxEmail>
			<cofaxAdmin>/admin/*</cofaxAdmin>
			<fileServlet>/static/*</fileServlet>
			<cofaxTools>/tools/*</cofaxTools>
		</servlet-mapping>
		<taglib>
			<taglib-uri>cofax.tld</taglib-uri>
			<taglib-location>/WEB-INF/tlds/cofax.tld</taglib-location>
		</taglib>
	</web-app>
</Object>

```

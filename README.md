# ASP.NET-Security
For Asp.NEt Security

## Web.Config
* [Custom Error Page](#Custom-Error)
* [Disabling TRACE,OPTIONS Method](#Disable-Methods)
* [ADD Custom Headers](#Custom-Headers)
* [Encrypt Viewstate](#Encrpt-Viewstate)




## Custom-Error
Below are some Custom Error page settings for different error codes

```config
<system.web>
    <compilation debug="false" targetFramework="4.6.1"/>
    <httpCookies requireSSL="true" />
    <customErrors mode="On" defaultRedirect="~/error.aspx">
      <error statusCode="400" redirect="~/error.aspx" />
      <error statusCode="401" redirect="~/error.aspx" />
      <error statusCode="403" redirect="~/error.aspx" />
      <error statusCode="404" redirect="~/error.aspx" />
      <error statusCode="408" redirect="~/error.aspx" />
      <error statusCode="500" redirect="~/error.aspx" />
      <error statusCode="503" redirect="~/error.aspx" />
    </customErrors>
</system.web>
  ```
  Alternative
  
  ```
  <!--<httpErrors errorMode="Custom">
      <remove statusCode="401" subStatusCode="-1" />
      <remove statusCode="403" subStatusCode="-1" />
      <remove statusCode="404" subStatusCode="-1" />
      <remove statusCode="500" subStatusCode="-1" />
      --><!-- full url when responsemode is Redirect --><!--
      <error statusCode="401" path="/Error.aspx" responseMode="Redirect" />
      --><!--local relative path when responsemode is ExecuteURL--><!--
      <error statusCode="403" path="/Error.aspx" responseMode="Redirect" />
      <error statusCode="404" path="/Error.aspx" responseMode="Redirect" />
      <error statusCode="500" path="/Error.aspx" responseMode="ExecuteURL" />
          </httpErrors>-->
    <httpErrors existingResponse="PassThrough">
	<error statusCode="400" path="~/error.aspx" responseMode="File"/>
	<error statusCode="401" path="~/error.aspx" responseMode="File"/>
	<error statusCode="404" path="~/error.aspx" responseMode="File"/>
	<error statusCode="500" path="~/error.aspx" responseMode="File"/>
    </httpErrors>

```
  
 ## Disable-Methods

```config
<system.webServer>
    <security>
      <requestFiltering>
        <verbs>
          <add verb="OPTIONS" allowed="false" />
          <add verb="TRACE" allowed="false" />
           <add verb="PUT" allowed="false" />
        </verbs>
      </requestFiltering>
    </security>
</system.webServer>
```

## Custom-Headers

```config
<configuration>
   <system.webServer>
      <httpProtocol>
         <customHeaders>
            <add name="X-Frame-options" value="MyCustomValue" />
			<add name="X-XSS-Protection" value="1; mode=block" />
			<add name="X-Content-Type-Options" value="nosniff" />
			<add name="X-Frame-Options" value="sameorigin" />
			<add name="X-Custom-Name" value="MyCustomValue" />
         </customHeaders>
      </httpProtocol>
   </system.webServer>
</configuration>
```

## Encrpt-Viewstate

this is simple way, THeres many encryption techniques
```config
<system.web> 
	<pages viewStateEncryptionMode="Always" /> 
</system.web>
```

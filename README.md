# ASP.NET-Security
For Asp.NEt Security

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

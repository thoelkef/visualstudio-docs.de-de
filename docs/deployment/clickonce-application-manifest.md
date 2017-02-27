---
title: "ClickOnce Application Manifest | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "application manifests [ClickOnce]"
  - "ClickOnce, application manifests"
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# ClickOnce Application Manifest
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifest ist eine XML\-Datei, die von einer Anwendung beschrieben, die mithilfe [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]bereitgestellt wird.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifeste verfügen über die folgenden Elemente und Attribute.  
  
|Element|Beschreibung|Attribute|  
|-------------|------------------|---------------|  
|[\<assembly\> Element](../deployment/assembly-element-clickonce-application.md)|Erforderlich.  Oberstes Element.|`manifestVersion`|  
|[\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-application.md)|Erforderlich.  Identifiziert die primäre Assembly der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<trustInfo\>\-Element](../deployment/trustinfo-element-clickonce-application.md)|Identifiziert die Sicherheitsanforderungen der Anwendung.|None|  
|[\<entryPoint\> Element](../deployment/entrypoint-element-clickonce-application.md)|Erforderlich.  Identifiziert den Anwendungscodeeinstiegspunkt.|`name`|  
|[\<dependency\> Element](../deployment/dependency-element-clickonce-application.md)|Erforderlich.  Identifiziert die zum Ausführen der Anwendung erforderlichen Abhängigkeiten.  Identifiziert optional Assemblys, die vorinstalliert werden müssen.|None|  
|[\<file\> Element](../deployment/file-element-clickonce-application.md)|Optional.  Identifiziert jede Nichtassemblydatei, die von der Anwendung verwendet wird.  Kann der Datei zugeordnete COM\-Isolationsdaten \(Component Object Model\) umfassen.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation\> Element](../deployment/fileassociation-element-clickonce-application.md)|Optional.  Gibt eine Dateierweiterung an, die der Anwendung zugeordnet sein soll.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## Hinweise  
 Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifestdatei identifiziert eine Anwendung, die mithilfe [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]bereitgestellt wird.  Weitere Informationen zu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] finden Sie unter [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
## Dateispeicherort  
 Ein Anwendungsmanifest ist [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] einer bestimmten Version einer Bereitstellung bestimmt.  Aus diesem Grund sollten sie separat gespeichert sind aus Bereitstellungsmanifesten.  Im Allgemeinen werden sie in einem Unterverzeichnis platziert, das nach der zugewiesenen Version benannt ist.  
  
 Das Anwendungsmanifest muss vor der Bereitstellung immer signiert werden.  Wenn Sie ein Anwendungsmanifest manuell ändern, müssen Sie das Anwendungsmanifest mit mage.exe erneut signieren, das Bereitstellungsmanifest aktualisieren und anschließend das Bereitstellungsmanifest erneut signieren.  Weitere Informationen finden Sie unter [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Dateinamensyntax  
 Der Name einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifestdatei sollte der vollständige Name und die Erweiterung der Anwendung, wie im `assemblyIdentity`\-Element identifiziert, gefolgt von der Erweiterung .manifest.  Beispielsweise verwendet ein auf die Anwendung Example.exe verweisendes Anwendungsmanifest die folgende Dateinamensyntax:  
  
 `example.exe.manifest`  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein Anwendungsmanifest für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung veranschaulicht.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />  
  <application />  
  <entryPoint>  
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
  <trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />  
        <defaultAssemblyRequest permissionSetReference="Custom" />  
      </applicationRequestMinimum>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <!--  
          UAC Manifest Options  
          If you want to change the Windows User Account Control level replace the   
          requestedExecutionLevel node with one of the following.  
  
        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />  
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />  
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />  
  
         If you want to utilize File and Registry Virtualization for backward   
         compatibility then delete the requestedExecutionLevel node.  
    -->  
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
  <dependency>  
    <dependentOS>  
      <osVersionInfo>  
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
      </osVersionInfo>  
    </dependentOS>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />  
    </dependentAssembly>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">  
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)
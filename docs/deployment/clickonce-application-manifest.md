---
title: ClickOnce-Anwendungsmanifest | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 7241995190c9384c1ed19cd4f9ae4cbf36f72f05
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="clickonce-application-manifest"></a>ClickOnce Application Manifest
Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifest ist eine XML-Datei, die eine Anwendung, die mit bereitgestellt wird, beschreibt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifeste haben die folgenden Elemente und Attribute.  
  
|Element|Beschreibung|Attribute|  
|-------------|-----------------|----------------|  
|[\<Assembly >-Element](../deployment/assembly-element-clickonce-application.md)|Erforderlich. Ein Element der obersten Ebene.|`manifestVersion`|  
|[\<AssemblyIdentity >-Element](../deployment/assemblyidentity-element-clickonce-application.md)|Erforderlich. Identifiziert die primäre Assembly von der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<TrustInfo >-Element](../deployment/trustinfo-element-clickonce-application.md)|Gibt die Sicherheitsanforderungen der Anwendung an.|Keiner|  
|[\<EntryPoint >-Element](../deployment/entrypoint-element-clickonce-application.md)|Erforderlich. Gibt den Einstiegspunkt der Anwendung Code an.|`name`|  
|[\<Dependency >-Element](../deployment/dependency-element-clickonce-application.md)|Erforderlich. Gibt jede Abhängigkeit an, die für die Ausführung der Anwendung erforderlich ist. Gibt optional Assemblys an, die vorinstalliert werden müssen.|Keiner|  
|[\<Datei >-Element](../deployment/file-element-clickonce-application.md)|Dies ist optional. Identifiziert jede Nichtassemblydatei, die von der Anwendung verwendet wird. Kann COM-Isolationsdaten (Component Object Model) enthalten, die der Datei zugeordnet sind.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<FileAssociation >-Element](../deployment/fileassociation-element-clickonce-application.md)|Dies ist optional. Gibt eine Erweiterung der Anwendung zugeordnet werden soll.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## <a name="remarks"></a>Hinweise  
 Die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifestdatei identifiziert eine Anwendung bereitgestellt, mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Weitere Informationen zu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] finden Sie unter [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Dateiort  
 Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifest für eine einzelne Version einer Bereitstellung spezifisch ist. Aus diesem Grund sollten sie getrennt von Bereitstellungsmanifesten gespeichert werden. Die allgemeine Konvention darin, diese in einem Unterverzeichnis mit dem Namen der zugewiesenen Version speichern.  
  
 Das Anwendungsmanifest muss vor der Bereitstellung immer signiert werden. Wenn Sie ein Anwendungsmanifest manuell ändern, müssen Sie mage.exe verwenden, um erneut signieren des Anwendungsmanifests, aktualisieren das Bereitstellungsmanifest, und klicken Sie dann das Bereitstellungsmanifest erneut signieren. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="file-name-syntax"></a>Dateinamensyntax  
 Der Name des eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifestdatei muss den vollständigen Namen und die Erweiterung der Anwendung, das in der `assemblyIdentity` -Element angegeben, gefolgt von der Erweiterung Manifest. Beispielsweise würde ein Anwendungsmanifest, das auf die Anwendung Example.exe verweist die folgende Syntax für Dateinamen verwenden.  
  
 `example.exe.manifest`  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird gezeigt, einem Anwendungsmanifest für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  
  
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
...  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
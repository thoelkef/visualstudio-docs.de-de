---
title: ClickOnce-Anwendungs Manifest | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adf5e160ec334859062311fae947ce34e79850d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157431"
---
# <a name="clickonce-application-manifest"></a>ClickOnce Application Manifest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungs Manifest ist eine XML-Datei, in der eine Anwendung beschrieben wird, die mithilfe von bereitgestellt wird [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungs Manifeste verfügen über die folgenden Elemente und Attribute.  
  
|Element|Beschreibung|Attribute|  
|-------------|-----------------|----------------|  
|[\<assembly>-Element](../deployment/assembly-element-clickonce-application.md)|Erforderlich. Ein Element der obersten Ebene.|`manifestVersion`|  
|[\<assemblyIdentity>-Element](../deployment/assemblyidentity-element-clickonce-application.md)|Erforderlich. Identifiziert die primäre Assembly der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[\<trustInfo>-Element](../deployment/trustinfo-element-clickonce-application.md)|Gibt die Sicherheitsanforderungen der Anwendung an.|Keine|  
|[\<entryPoint>-Element](../deployment/entrypoint-element-clickonce-application.md)|Erforderlich. Identifiziert den Einstiegspunkt für den Anwendungscode.|`name`|  
|[\<dependency>-Element](../deployment/dependency-element-clickonce-application.md)|Erforderlich. Gibt jede Abhängigkeit an, die für die Ausführung der Anwendung erforderlich ist. Gibt optional Assemblys an, die vorinstalliert werden müssen.|Keine|  
|[\<file>-Element](../deployment/file-element-clickonce-application.md)|Optional. Identifiziert jede nicht Assemblydatei, die von der Anwendung verwendet wird. Kann COM-Isolationsdaten (Component Object Model) enthalten, die der Datei zugeordnet sind.|`name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType`|  
|[\<fileAssociation>-Element](../deployment/fileassociation-element-clickonce-application.md)|Optional. Gibt eine Dateierweiterung an, die der Anwendung zugeordnet werden soll.|`extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon`|  
  
## <a name="remarks"></a>Bemerkungen  
 Die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungs Manifest-Datei identifiziert eine mithilfe von bereitgestellte Anwendung [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Weitere Informationen zu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] finden Sie unter [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Dateispeicherort  
 Ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungs Manifest ist für eine einzelne Version einer Bereitstellung spezifisch. Aus diesem Grund sollten Sie getrennt von Bereitstellungs Manifesten gespeichert werden. Die gängige Konvention besteht darin, Sie in einem Unterverzeichnis zu platzieren, das nach der zugehörigen Version benannt ist.  
  
 Das Anwendungs Manifest muss vor der Bereitstellung immer signiert werden. Wenn Sie ein Anwendungs Manifest manuell ändern, müssen Sie mage.exe zum erneuten Signieren des Anwendungs Manifests verwenden, das Bereitstellungs Manifest aktualisieren und dann das Bereitstellungs Manifest erneut signieren. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="file-name-syntax"></a>Dateinamensyntax  
 Der Name einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungs Manifest-Datei muss der vollständige Name und die Erweiterung der Anwendung sein, wie im- `assemblyIdentity` Element angegeben, gefolgt von der Erweiterung. manifest. Beispielsweise würde ein Anwendungs Manifest, das auf die Example.exe Anwendung verweist, die folgende Dateiname-Syntax verwenden.  
  
 `example.exe.manifest`  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt ein Anwendungs Manifest für eine- [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)

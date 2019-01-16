---
title: '&lt;FileAssociation&gt; -Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78cdb22f2d87b67d5a29e8031358193526fa4b71
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866162"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;FileAssociation&gt; -Element (ClickOnce-Anwendung)
Gibt eine Dateierweiterung mit der Anwendung zugeordnet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `fileAssociation`-Element ist optional. Das Element weist folgende Attribute auf.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`extension`|Erforderlich. Die Dateierweiterung der Anwendung zugeordnet werden soll.|  
|`description`|Erforderlich. Eine Beschreibung des Dateityps für die Verwendung von der Shell.|  
|`progid`|Erforderlich. Ein Name, den Dateityp eindeutig identifiziert.|  
|`defaultIcon`|Erforderlich. Gibt das Symbol für Dateien mit dieser Erweiterung verwenden. Die Symboldatei muss angegeben werden, mithilfe der [ \<Datei > Element](../deployment/file-element-clickonce-application.md) innerhalb der [ \<Assembly >-Element](../deployment/assembly-element-clickonce-application.md) , enthält dieses Element.|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element muss enthalten einen XML-Namespace-Verweis auf "Urn: Schemas-Microsoft-com:clickonce.v1". Wenn die `<fileAssociation>` Element wird verwendet, müssen sie nach dem stammen die `<application>` Element in seinem übergeordneten [ \<Assembly >-Element](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] überschreibt keine vorhandenen dateizuordnungen. Eine ClickOnce-Anwendung kann jedoch die Dateierweiterung für den aktuellen Benutzer überschreiben. Nach der Deinstallation der ClickOnce-Anwendung ClickOnce löscht die dateizuordnung für den Benutzer und die Zuordnung pro Computer wieder aktiv ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, `fileAssociation` Elemente in einer Anwendung für eine Text-Editor-Anwendung bereitgestellt wird, mithilfe von manifest [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Dieses Codebeispiel enthält auch die [ \<Datei >-Element](../deployment/file-element-clickonce-application.md) erforderlich die `defaultIcon` Attribut.  
  
```xml  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
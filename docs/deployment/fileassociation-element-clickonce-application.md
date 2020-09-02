---
title: '&lt;fileAssociation- &gt; Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d3a43af5b2c7d50034cbed9d7da16e65b402f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928522"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation- &gt; Element (ClickOnce-Anwendung)
Gibt eine Dateierweiterung an, die der Anwendung zugeordnet werden soll.

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

|attribute|Beschreibung|
|---------------|-----------------|
|`extension`|Erforderlich. Die Dateierweiterung, die der Anwendung zugeordnet werden soll.|
|`description`|Erforderlich. Eine Beschreibung des Dateityps, der von der Shell verwendet werden soll.|
|`progid`|Erforderlich. Ein Name, der den Dateityp eindeutig identifiziert.|
|`defaultIcon`|Erforderlich. Gibt das Symbol an, das für Dateien mit dieser Erweiterung verwendet werden soll. Die Symbol Datei muss mithilfe des- [ \<file> Elements](../deployment/file-element-clickonce-application.md) innerhalb des [-Elements angegeben werden, das \<assembly> ](../deployment/assembly-element-clickonce-application.md) dieses Element enthält.|

## <a name="remarks"></a>Bemerkungen
 Dieses Element muss einen XML-Namespace Verweis auf "urn: Schemas-Microsoft-com: ClickOnce. v1" enthalten. Wenn das- `<fileAssociation>` Element verwendet wird, muss es hinter dem- `<application>` Element in seinem übergeordneten [ \<assembly> Element](../deployment/assembly-element-clickonce-application.md)stehen.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vorhandene Dateizuordnungen werden von nicht überschrieben. Allerdings kann eine ClickOnce-Anwendung die Dateierweiterung nur für den aktuellen Benutzer überschreiben. Nachdem diese ClickOnce-Anwendung deinstalliert wurde, löscht ClickOnce die Datei Zuordnung für den Benutzer, und die Zuordnung pro Computer ist wieder aktiv.

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht `fileAssociation` Elemente in einem Anwendungs Manifest für eine mit bereitgestellte Text-Editor-Anwendung [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Dieses Codebeispiel enthält auch das- [ \<file> Element](../deployment/file-element-clickonce-application.md) , das für das-Attribut erforderlich ist `defaultIcon` .

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

## <a name="see-also"></a>Weitere Informationen
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
---
title: VSIXLanguagePack-Element (VSIX-Sprachpaket Schema) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd3ed1477d1c4d345e5fc6f6496d12044d4af244
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114231"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>VSIXLanguagePack-Element (Schema für das VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erforderlich. Stellt das Stamm Element für ein VSIX-Sprachpaket bereit. Das VSIX-Sprachpaket enthält lokalisierte Installationsinformationen für ein VSIX-Paket.  
  
## <a name="syntax"></a>Syntax  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`xmlns`|Der XML-Namespace, in dem das VSIX-Sprachpaket Schema definiert ist.|  
  
## <a name="xmlns-attribute"></a>xmlns-Attribut  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Erforderlich. Der Speicherort der Datei, die das Schema für Sprachpakete definiert.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[LocalizedName-Element](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Erforderlich. Der lokalisierte Name der zu installierenden Erweiterung.|  
|[LocalizedDescription-Element](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Erforderlich. Die lokalisierte Beschreibung der zu installierenden Erweiterung.|  
|[MoreInfoURL-Element](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Dies ist optional. Ein Link zu lokalisierten Informationen über die Erweiterung.|  
|[License-Element](../extensibility/license-element-vsix-language-pack-schema.md)|Dies ist optional. Der Pfad einer lokalisierten Version der Lizenzdatei für die Erweiterung.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keine||  
  
## <a name="element-information"></a>Elementinformationen  

:::row:::
    :::column:::
        Namespace
    :::column-end:::
    :::column:::
        `http://schemas.microsoft.com/developer/vsx-schema-lp/2010`
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Name des Schemas
    :::column-end:::
    :::column:::
        VSIX-Sprachpaket Schema
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Validierungsdatei
    :::column-end:::
    :::column:::
        Vsixlanguagepackschema. xsd
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Kann leer sein
    :::column-end:::
    :::column:::
        Nein
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>Weitere Informationen  
 [VSX Language Pack Schema Referenz](../extensibility/vsx-language-pack-schema-reference.md) [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md) [VSIX-Erweiterungs Schema 1,0 Referenz](/previous-versions/dd393700(v=vs.110))

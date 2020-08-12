---
title: LocalizedName-Element (VSIX-Sprachpaket Schema) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64d8430dbcf563ca232d1b8d850678925770219f
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114176"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>LocalizedName-Element (Schema für das VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erforderlich. Der lokalisierte Name der zu installierenden Erweiterung.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Keine||  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keine||  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[VSIX-LanguagePack-Element](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Erforderlich. Stellt das Stamm Element für ein VSIX-Sprachpaket bereit.|  
  
## <a name="text-value"></a>Textwert  
 Erforderlich. Der Name des Sprachpakets in der Zielsprache.  
  
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
        Nicht verfügbar
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Referenz für das VSX-Sprachpaket](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)   
 [VSIX-Erweiterungs Schema 1,0-Referenz](/previous-versions/dd393700(v=vs.110))

---
title: Localizeddescription-Element (VSIX-Sprachpaket Schema) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b4eb077ba8c957466568967804487929254117e
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114186"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>LocalizedDescription-Element (Schema für das VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erforderlich. Stellt eine lokalisierte Beschreibung der Erweiterung bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
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
 Erforderlich. Eine Textbeschreibung der Erweiterung in der Zielsprache.  
  
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

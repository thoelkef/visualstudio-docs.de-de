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
ms.openlocfilehash: 58e491290122a9d525ff8129333ac0f52ac5f778
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477038"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>LocalizedName-Element (Schema für das VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erforderlich. Der lokalisierte Name der zu installierenden Erweiterung.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden die Attribute, untergeordneten und übergeordneten Elemente beschrieben.  
  
### <a name="attributes"></a>Attributes  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|Keine||  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|Keine||  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|[VSIX-LanguagePack-Element](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Erforderlich. Stellt das Stamm Element für ein VSIX-Sprachpaket bereit.|  
  
## <a name="text-value"></a>Textwert  
 Erforderlich. Der Name des Sprachpakets in der Zielsprache.  
  
## <a name="element-information"></a>Elementinformationen  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Namespace    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Name des Schemas   |                 VSIX-Sprachpaket Schema                 |
| Validierungsdatei |                VSIXLanguagePackSchema.xsd                 |
|  Kann leer sein   |                      Nicht verfügbar                       |
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Referenz für das VSX-Sprachpaket](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)   
 [VSIX-Erweiterungs Schema 1,0-Referenz](/previous-versions/dd393700(v=vs.110))

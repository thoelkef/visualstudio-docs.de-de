---
title: LocalizedName-Element (Schema für VSIX-Sprachpaket) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d17ce9db334d3b2cc8b6c892784b10d42eba07ad
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832419"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>LocalizedName-Element (Schema für VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erforderlich. Der lokalisierte Name der Erweiterung installiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Keiner||  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keiner||  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[VSIX-LanguagePack-Element](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Erforderlich. Stellt das Stammelement für ein VSIX-Sprachpaket bereit.|  
  
## <a name="text-value"></a>Textwert  
 Erforderlich. Der Name des Language Packs in der Zielsprache.  
  
## <a name="element-information"></a>Elementinformationen  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Namespace    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Schemaname   |                 Schema für das VSIX-Sprachpaket                 |
| Validierungsdatei |                VSIXLanguagePackSchema.xsd                 |
|  Leer kann sein   |                      Nicht zutreffend                       |
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz für VSX Sprachpaket](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)   
 [Referenz zum VSIX-Erweiterung Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)


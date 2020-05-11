---
title: License-Element (Schema für das VSIX-Sprachpaket) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1299d97cbda78049732d3367a9231272397e2ec
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477072"
---
# <a name="license-element-vsix-language-pack-schema"></a>License-Element (Schema für das VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Optional. Der Pfad einer lokalisierten Version der Lizenzdatei für die Erweiterung.  
  
## <a name="syntax"></a>Syntax  
  
```  
<License>FilePath\license.txt</License>  
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
 Der relative Pfad der lokalisierten Lizenzdatei, die angezeigt werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn das `License`-Element definiert ist, wird der Text der angegebenen Lizenzdatei während des Setups angezeigt, und der Benutzer muss die Lizenz akzeptieren, um den Vorgang fortzusetzen.  
  
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

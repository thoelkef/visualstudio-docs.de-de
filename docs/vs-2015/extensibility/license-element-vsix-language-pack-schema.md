---
title: Lizenz-Element (Schema für VSIX-Sprachpaket) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ecf1913878137d84346275beccb512027f74f8f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514563"
---
# <a name="license-element-vsix-language-pack-schema"></a>License-Element (Schema für VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [License-Element (Schema für VSIX-Sprachpaket)](https://docs.microsoft.com/visualstudio/extensibility/license-element-vsix-language-pack-schema).  
  
Dies ist optional. Der Pfad einer lokalisierten Version der Lizenzdatei für die Erweiterung.  
  
## <a name="syntax"></a>Syntax  
  
```  
<License>FilePath\license.txt</License>  
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
 Der relative Pfad der lokalisierten Lizenzdatei, die angezeigt werden.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die `License` Element definiert ist, wird der Text der angegebenen Lizenzdatei während des Setups angezeigt, und der Benutzer muss akzeptieren der Lizenz, um den Vorgang fortzusetzen.  
  
## <a name="element-information"></a>Elementinformationen  
  
|||  
|-|-|  
|Namespace|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|Schemaname|Schema für das VSIX-Sprachpaket|  
|Validierungsdatei|VSIXLanguagePackSchema.xsd|  
|Leer kann sein|Nicht zutreffend|  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz für VSX Sprachpaket](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)   
 [Referenz zum VSIX-Erweiterung Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)


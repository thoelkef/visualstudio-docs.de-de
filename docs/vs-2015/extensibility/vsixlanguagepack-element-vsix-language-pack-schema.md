---
title: VSIXLanguagePack-Element (Schema für VSIX-Sprachpaket) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf8e55e38ecf16577482955c30ea95c5a5980087
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515358"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>VSIXLanguagePack-Element (Schema für VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [VSIXLanguagePack-Element (Schema für VSIX-Sprachpaket)](https://docs.microsoft.com/visualstudio/extensibility/vsixlanguagepack-element-vsix-language-pack-schema).  
  
Erforderlich. Stellt das Stammelement für ein VSIX-Sprachpaket bereit. Das VSIX-Sprachpaket enthält lokalisierte Installationsinformationen für ein VSIX-Paket.  
  
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
|`xmlns`|Der XML-Namespace, in dem das VSIX-Sprachpaket-Schema definiert ist.|  
  
## <a name="xmlns-attribute"></a>Xmlns-Attribut  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Erforderlich. Der Speicherort der Datei, die das Schema für die Language Packs definiert.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[LocalizedName-Element](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Erforderlich. Der lokalisierte Name der Erweiterung installiert werden.|  
|[LocalizedDescription-Element](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Erforderlich. Die lokalisierte Beschreibung der Erweiterung installiert werden.|  
|[MoreInfoURL-Element](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Dies ist optional. Ein Link zum lokalisierte Informationen über die Erweiterung.|  
|[License-Element](../extensibility/license-element-vsix-language-pack-schema.md)|Dies ist optional. Der Pfad einer lokalisierten Version der Lizenzdatei für die Erweiterung.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keiner||  
  
## <a name="element-information"></a>Elementinformationen  
  
|||  
|-|-|  
|Namespace|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|Schemaname|Schema für das VSIX-Sprachpaket|  
|Validierungsdatei|VSIXLanguagePackSchema.xsd|  
|Leer kann sein|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz für VSX Sprachpaket](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)   
 [Referenz zum VSIX-Erweiterung Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)


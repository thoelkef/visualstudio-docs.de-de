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
ms.openlocfilehash: 91f0792f64e09292836a3b2d60f669c67903b3a7
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114171"
---
# <a name="license-element-vsix-language-pack-schema"></a>License-Element (Schema für das VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Der relative Pfad der lokalisierten Lizenzdatei, die angezeigt werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn das- `License` Element definiert ist, wird der Text der angegebenen Lizenzdatei während des Setups angezeigt, und der Benutzer muss die Lizenz akzeptieren, um den Vorgang fortzusetzen.  
  
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

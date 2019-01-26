---
title: Verweist auf Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 454f8a0da24d331456eb3c638512257868a19c69
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949011"
---
# <a name="references-element-visual-studio-templates"></a>References-Element (Visual Studio-Vorlagen)
Gruppiert die Verweise der Assembly, die die Vorlage zu Projekten hinzugefügt.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Verweise >  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Verweis](../extensibility/reference-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Assemblyverweis an, der hinzugefügt wird, wenn das Element einem Projekt hinzugefügt wird. Es muss mindestens eine `Reference` Elemente in einer `References` Element.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage.|  
  
## <a name="remarks"></a>Hinweise  
 `References` ist ein optionales untergeordnetes Element von `TemplateContent`.  
  
 Die `Reference` und `References` Elemente können nur verwendet werden, *VSTEMPLATE* Dateien mit einer `Type` -Attributwert `Item`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die `TemplateContent` Element einer Elementvorlage. Dieser XML-Code fügt Verweise auf die *"System.dll"* und *"System.Data.dll"* Assemblys.  
  
```xml  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlage](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)

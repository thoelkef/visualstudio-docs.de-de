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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0da362b5c054ba5bb9b7266a3508ea73ca8dcaf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53884568"
---
# <a name="references-element-visual-studio-templates"></a>References-Element (Visual Studio-Vorlagen)
Gruppiert die Verweise der Assembly, die die Vorlage zu Projekten hinzugefügt.  
  
 \<VSTemplate>  
 \<TemplateContent >  
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

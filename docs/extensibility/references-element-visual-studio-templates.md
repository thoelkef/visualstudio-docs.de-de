---
title: "References-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#References"
helpviewer_keywords: 
  - "<References>-Element [Visual Studio-Vorlagen]"
  - "References-Element [Visual Studio-Vorlagen]"
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# References-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gruppiert die Assemblyverweise, die Projekten von der Vorlage hinzugefügt werden.  
  
## Syntax  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Verweise](../extensibility/reference-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Assemblyverweis an, der hinzugefügt werden soll, wenn das Element in ein Projekt aufgenommen wird.  Mindestens ein `Reference`\-Element muss in einem `References`\-Element enthalten sein.|  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage an.|  
  
## Hinweise  
 `References` ist ein optionales untergeordnetes Element von `TemplateContent`.  
  
 Das `Reference`\-Element und das `References`\-Element können nur in VSTEMPLATE\-Dateien verwendet werden, die über den `Type`\-Attributwert `Item` verfügen.  
  
## Beispiel  
 Im folgenden Beispiel wird das `TemplateContent`\-Element einer Elementvorlage veranschaulicht.  Durch diesen XML\-Code werden Verweise auf die Assemblys System.dll und System.Data.dll hinzugefügt.  
  
```  
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
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
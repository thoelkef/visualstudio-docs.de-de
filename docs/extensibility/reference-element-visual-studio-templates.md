---
title: "Reference-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Reference"
helpviewer_keywords: 
  - "<Reference>-Element [Visual Studio-Vorlagen]"
  - "Reference-Element [Visual Studio-Vorlagen]"
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Reference-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt den Assemblyverweis an, der hinzugefügt werden soll, wenn das Element in ein Projekt aufgenommen wird.  
  
## Syntax  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt Informationen zu einer Assembly an, über die die Vorlage Projekten einen Verweis dieser Assembly hinzufügt.  Es muss ein `Assembly`\-Element in jedem `Reference`\-Element vorhanden sein.|  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Verweise](../extensibility/references-element-visual-studio-templates.md)|Gruppiert die Assemblyverweise, die Projekten von der Vorlage hinzugefügt werden.|  
  
## Hinweise  
 `Reference` ist ein erforderliches untergeordnetes Element von `References`.  
  
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
---
title: "Assembly-Element (Visual Studio-Vorlagen) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Assembly"
helpviewer_keywords: 
  - "Assembly-Element [Visual Studio-Vorlagen]"
  - "<Assembly>-Element [Visual Studio-Vorlagen]"
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Assembly-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt Informationen zu einer Assembly an, über die die Vorlage Projekten einen Verweis dieser Assembly hinzufügt.  
  
## Syntax  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Verweise](../extensibility/reference-element-visual-studio-templates.md)|Gibt den Assemblyverweis an, der hinzugefügt werden soll, wenn das Element in ein Projekt aufgenommen wird.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Dieser Text gibt die Assembly an, die einem Projekt beim Instanziieren der Elementvorlage hinzugefügt werden soll.  Dieser Assemblyname muss auf eine der folgenden Weisen angegeben werden:  
  
-   Als vollständiger Assemblyname.  Beispiel:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Als einfacher Textverweis.  Beispiel:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## Hinweise  
 `Assembly` ist ein erforderliches untergeordnetes Element von `Reference`.  
  
 Die Elemente `Reference`, `References,` und `Assembly` können nur in VSTEMPLATE\-Dateien verwendet werden, die über den `Type`\-Attributwert `Item` verfügen.  
  
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
---
title: "CustomParameters-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters"
helpviewer_keywords: 
  - "CustomParameters-Element [Visual Studio-Projektvorlagen]"
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# CustomParameters-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gruppiert die benutzerdefinierten Parameter, die an dem Vorlagen\-Assistenten übergeben werden, wenn der Assistent Parameter Austausch vornimmt.  
  
## Syntax  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Enthält einen benutzerdefinierten Parameternamen und den Wert, der verwendet wird, wenn ein Projekt oder Element von der Vorlage erstellt wird. Es kann keine oder mehrere `CustomParameter`\-Elemente in einem `CustomParameters`\-Element geben.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage.|  
  
## Hinweise  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mehrere benutzerdefinierte Parameter in einer Vorlage zu verwenden. Wenn ein Projekt oder Element mit den folgenden benutzerdefinierten Parametern, alle Instanzen der von einer Vorlage erstellt wird `$color1$` und `$color2$` in der Vorlage die Dateien ersetzt werden, mit `Red` und `Blue`, bzw..  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## Siehe auch  
 [CustomParameter\-Element \(Visual Studio\-Vorlagen\)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
---
title: "CustomParameter-Element (Visual Studio-Vorlagen) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter"
helpviewer_keywords: 
  - "CustomParameters-Element [Visual Studio-Projektvorlagen]"
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# CustomParameter-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enthält einen benutzerdefinierten Parameternamen und \-wert, der beim Erstellen eines Projekts oder Elements von der Vorlage verwendet wird.  
  
## Syntax  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Erforderlich.  Der Name des Parameters.  Das Format für Parameter lautet $*name*$.|  
|`Value`|Erforderlich.  Der Ersetzungswert für den Parameter.|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Gruppiert die benutzerdefinierten Parameter, die an den Vorlagen\-Assistenten übergeben werden sollen, wenn der Assistent Parameterersetzungen vornimmt.|  
  
## Hinweise  
 Wenn eine Vorlage `CustomParameter`\-Elemente enthält, wird jede Instanz des `Name`\-Attributs durch das `Value`\-Attribut in den erstellten Projekt\- oder Elementdateien ersetzt.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mehrere benutzerdefinierte Parameter in einer Vorlage verwendet werden.  Wenn ein Projekt oder Element mit den folgenden benutzerdefinierten Parametern von einer Vorlage erstellt wird, werden alle Instanzen von `$color1$` und `$color2$` in den Vorlagendateien durch `Red` bzw. `Blue` ersetzt.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## Siehe auch  
 [CustomParameters\-Element \(Visual Studio\-Vorlagen\)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
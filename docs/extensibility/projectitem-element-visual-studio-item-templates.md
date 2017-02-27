---
title: "ProjectItem-Element (Visual Studio-Elementvorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem>-Element [Visual Studio-Projektelementvorlagen]"
  - "ProjectItem-Element [Visual Studio-Projektelementvorlagen]"
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# ProjectItem-Element (Visual Studio-Elementvorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt eine Datei an, die in der Elementvorlage enthalten ist.  
  
> [!NOTE]
>  Je nachdem, ob die Vorlage für ein Projekt oder ein Element entwickelt wurde, akzeptiert das `ProjectItem`\-Element verschiedene Attribute.  In diesem Thema wird das `ProjectItem`\-Element für Elementvorlagen erläutert.  Eine Erläuterung des `ProjectItem`\-Elements für Projektvorlagen finden Sie unter [ProjectItem\-Element \(Visual Studio\-Projektvorlagen\)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
## Syntax  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Description|  
|--------------|-----------------|  
|`SubType`|Optionales Attribut.<br /><br /> Gibt den Untertyp eines Elements in einer Elementvorlage mit mehreren Dateien an.  Durch diesen Wert wird der Editor angegeben, mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] das Element öffnet.|  
|`CustomTool`|Optionales Attribut.<br /><br /> Legt das CustomTool für das Element in der Projektdatei fest.|  
|`ItemType`|Optionales Attribut.<br /><br /> Legt den ItemType für das Element in der Projektdatei fest.|  
|`ReplaceParameters`|Optionales Attribut.<br /><br /> Ein boolescher Wert, durch den angegeben wird, ob das Element über Parameterwerte verfügt, die ersetzt werden müssen, wenn ein Projekt von der Vorlage erstellt wird.  Der Standardwert lautet `false`.|  
|`TargetFileName`|Optionales Attribut.<br /><br /> Gibt den Namen des Elements an, das von der Vorlage erstellt wird.  Dieses Attribut ist hilfreich, wenn ein Elementname mittels Parameterersetzung erstellt werden soll.|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage an.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 `string` mit dem Namen einer Datei, die in der ZIP\-Datei der Vorlage enthalten ist.  
  
## Hinweise  
 `ProjectItem` ist ein optionales untergeordnetes Element von `TemplateContent`.  
  
 Das `TargetFileName`\-Attribut kann zum Umbenennen von Dateien mit Parametern verwendet werden.  Wenn die Datei `MyFile.vb` im Stammverzeichnis der ZIP\-Datei der Vorlage vorhanden ist, sie jedoch nach dem Dateinamen benannt werden soll, der vom Benutzer im Dialogfeld **Neues Element hinzufügen** eingegeben wurde, würden Sie beispielsweise folgenden XML\-Code verwenden:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Wenn ein Element auf der Grundlage dieser Vorlage erstellt wird, entspricht der Dateiname dem Namen, den der Benutzer im Dialogfeld **Neues Element hinzufügen** eingegeben hat.  Dies ist hilfreich, wenn Elementvorlagen mit mehreren Dateien erstellt werden.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Elementvorlagen mit mehreren Dateien](../ide/how-to-create-multi-file-item-templates.md) und [Vorlagenparameter](../ide/template-parameters.md).  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für die Standardelementvorlage einer Klasse in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Elementvorlagen mit mehreren Dateien](../ide/how-to-create-multi-file-item-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)
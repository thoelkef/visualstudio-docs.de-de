---
title: "Project-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Project"
helpviewer_keywords: 
  - "<Project>-Element [Visual Studio-Vorlagen]"
  - "Project-Element [Visual Studio-Vorlagen]"
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Project-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt die Dateien oder Verzeichnisse an, die dem Projekt hinzugefügt werden sollen.  
  
## Syntax  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Description|  
|--------------|-----------------|  
|`File`|Erforderliches Attribut.<br /><br /> Gibt den Namen der Projektdatei in der ZIP\-Datei der Vorlage an.|  
|`ReplaceParameters`|Optionales Attribut.<br /><br /> Ein boolescher Wert, durch den angegeben wird, ob die Projektdatei über Parameterwerte verfügt, die beim Erstellen des Projekts von der Vorlage ersetzt werden müssen.  Der Standardwert lautet `false`.|  
|`TargetFileName`|Optionales Attribut.<br /><br /> Gibt bei der Projekterstellung von der Vorlage den Namen der Projektdatei an.|  
|`IgnoreProjectParameter`|Optionales Attribut.<br /><br /> Gibt an, ob das Projekt zur aktuellen Projektmappe hinzugefügt werden soll.  Wenn der Wert des benutzerdefinierten Parameters, "$*myCustomParameter*$" in der Parameterersatzdatei vorhanden ist, wird das Projekt erstellt, aber hinzugefügt nicht als Teil der aktuell geöffneten Projektmappe.|  
  
### Untergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Ordner](../extensibility/folder-element-visual-studio-project-templates.md)|Optionales Element.<br /><br /> Gibt einen Ordner an, der dem Projekt hinzugefügt werden soll.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Optionales Element.<br /><br /> Gibt eine Datei an, die einem Projekt hinzugefügt werden soll.|  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Erforderliches Element.|  
  
## Hinweise  
 `Project` ist ein optionales untergeordnetes Element von `TemplateContent`.  
  
 Das `Project`\-Element wird zum Festlegen eines Projekts verwendet und ist daher nur in Projektvorlagen gültig.  
  
 `Project`\-Elemente können über untergeordnete [Folder](../extensibility/folder-element-visual-studio-project-templates.md)\-Elemente oder untergeordnete [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)\-Elemente, nicht aber über eine Mischung aus untergeordneten `Folder`\-Elementen und untergeordneten `ProjectItem`\-Elementen verfügen.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] benennt die Projektdatei automatisch um und verwendet dabei den Namen, den der Benutzer im Dialogfeld **Neues Projekt** eingegeben hat.  Verwenden Sie das `TargetFileName`\-Attribut, wenn Sie einen alternativen Dateinamen für die mit der Vorlage erstellten Projektdateien eingeben möchten.  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Anwendung veranschaulicht.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [ProjectItem\-Element \(Visual Studio\-Projektvorlagen\)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder\-Element \(Visual Studio\-Projektvorlagen\)](../extensibility/folder-element-visual-studio-project-templates.md)
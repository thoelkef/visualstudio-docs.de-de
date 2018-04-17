---
title: Project-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ef09516237ad30a18f9790ddae40260d834af21
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="project-element-visual-studio-templates"></a>Project-Element (Visual Studio-Vorlagen)
Gibt an, die Dateien oder Verzeichnisse zu dem Projekt hinzugefügt.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Project>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`File`|Erforderliches Attribut.<br /><br /> Gibt den Namen der Projektdatei in der ZIP-Vorlagendatei.|  
|`ReplaceParameters`|Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob die Projektdatei Parameterwerte verfügt, die ersetzt werden muss, wenn ein Projekt aus der Vorlage erstellt wird. Der Standardwert ist `false`sein.|  
|`TargetFileName`|Optionales Attribut.<br /><br /> Gibt den Namen der Projektdatei an, wenn ein Projekt aus der Vorlage erstellt wird.|  
|`IgnoreProjectParameter`|Optionales Attribut.<br /><br /> Gibt an, ob das Projekt der aktuellen Projektmappe hinzugefügt werden soll. Wenn der Wert der benutzerdefinierten Parameter "$*MyCustomParameter*$" vorhanden ist in der Parameterdatei Ersatz das Projekt wird erstellt, aber nicht als Teil der gerade geöffneten Projektmappe hinzugefügt.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Ordner](../extensibility/folder-element-visual-studio-project-templates.md)|Optionales Element.<br /><br /> Gibt einen Ordner auf dem Projekt hinzugefügt.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Optionales Element.<br /><br /> Gibt eine Datei zu einem Projekt hinzugefügt.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Erforderliches Element.|  
  
## <a name="remarks"></a>Hinweise  
 `Project` ist ein optionales untergeordnetes Element von `TemplateContent`.  
  
 Die `Project` Element wird zum Angeben eines Projekts verwendet und ist daher nur in Projektvorlagen gültig.  
  
 `Project` Elemente können besitzen [Ordner](../extensibility/folder-element-visual-studio-project-templates.md) untergeordnete Elemente oder [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) untergeordnete Elemente, aber keine Kombination aus beiden `Folder` und `ProjectItem` untergeordnete Elemente.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Benennt automatisch in der Projektdateiname anhand des Namens eingegeben haben, vom Benutzer in der **neues Projekt** (Dialogfeld). Verwenden der `TargetFileName` Attribut, wenn Sie einen alternativen Dateinamen für die mit der Vorlage erstellten Projektdateien bereitstellen möchten.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Anwendung veranschaulicht.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [ProjectItem-Element (Visual Studio-Projektvorlagen)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder-Element (Visual Studio-Projektvorlagen)](../extensibility/folder-element-visual-studio-project-templates.md)
---
title: Project-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
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
ms.openlocfilehash: c74868621725d916177df73f648766f706b71d40
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950328"
---
# <a name="project-element-visual-studio-templates"></a>Project-Element (Visual Studio-Vorlagen)
Gibt an, die Dateien oder Verzeichnisse dem Projekt hinzu.  
  
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
|`File`|Erforderliches Attribut.<br /><br /> Gibt den Namen der Projektdatei in der Vorlage *ZIP* Datei.|  
|`ReplaceParameters`|Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob die Projektdatei Parameterwerte verfügt, die ersetzt werden muss, wenn ein Projekt aus der Vorlage erstellt wird. Der Standardwert ist `false`sein.|  
|`TargetFileName`|Optionales Attribut.<br /><br /> Gibt den Namen der Projektdatei an, wenn ein Projekt aus der Vorlage erstellt wird.|  
|`IgnoreProjectParameter`|Optionales Attribut.<br /><br /> Gibt an, ob das Projekt der aktuellen Projektmappe hinzugefügt werden soll. Wenn der Wert der benutzerdefinierten Parameter "$*MyCustomParameter*$" vorhanden ist in der Parameterdatei ersetzen, das Projekt erstellt werden, jedoch nicht als Teil der aktuell geöffneten Projektmappe hinzugefügt.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Ordner](../extensibility/folder-element-visual-studio-project-templates.md)|Optionales Element.<br /><br /> Gibt einen Ordner auf dem Projekt hinzugefügt.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Optionales Element.<br /><br /> Gibt eine Datei zu einem Projekt hinzufügen.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Erforderliches Element.|  
  
## <a name="remarks"></a>Hinweise  
 `Project` ist ein optionales untergeordnetes Element von `TemplateContent`.  
  
 Die `Project` Element wird zum Festlegen ein Projekts verwendet werden soll, und aus diesem Grund ist nur gültig, in-Projektvorlagen.  
  
 `Project` Elemente können besitzen [Ordner](../extensibility/folder-element-visual-studio-project-templates.md) untergeordnete Elemente oder [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) untergeordnete Elemente, aber nicht auf einer Kombination dieser beiden `Folder` und `ProjectItem` untergeordneten Elemente.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Benennt automatisch auf Grundlage des Namens eingegeben haben, vom Benutzer im Namen der Projektdatei die **neues Projekt** Dialogfeld. Verwenden der `TargetFileName` Attribut, wenn Sie einen alternativer Dateiname für Projektdateien, die mit der Vorlage erstellte bereitstellen möchten.  
  
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
 [Schemareferenz zu Visual Studio-Vorlage](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [ProjectItem-Element (Visual Studio-Projektvorlagen)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder-Element (Visual Studio-Projektvorlagen)](../extensibility/folder-element-visual-studio-project-templates.md)
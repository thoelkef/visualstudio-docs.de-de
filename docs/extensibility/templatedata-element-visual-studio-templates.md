---
title: TemplateData-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9b5ae3111691658f9748ba8677ea67ca6e216714
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561839"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData-Element (Visual Studio-Vorlagen)
Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.  
  
 \<VSTemplate>  
 \<TemplateData>  
  
## <a name="syntax"></a>Syntax  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
| Element | Beschreibung |
| - | - |
| [Name](../extensibility/name-element-visual-studio-templates.md) | Erforderliches Element.<br /><br /> Der Name der Vorlage gibt an, wie er in einem angezeigt wird der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld. |
| [Beschreibung](../extensibility/description-element-visual-studio-templates.md) | Erforderliches Element.<br /><br /> Gibt die Beschreibung der Vorlage an, wie er in einem angezeigt wird der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld. |
| [Symbol](../extensibility/icon-element-visual-studio-templates.md) | Erforderliches Element.<br /><br /> Gibt den Pfad und den Dateinamen der Bilddatei, die als Symbol dient entweder angezeigt wird, die **neues Projekt** oder **neues Element hinzufügen** im Dialogfeld für die Vorlage. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Erforderliches Element.<br /><br /> Kategorisiert die Projektvorlage, sodass es unter der angegebenen Gruppe angezeigt wird der **neues Projekt** Dialogfeld. |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Klassifiziert die Projektvorlage, sodass es unter der angegebenen Unterkategorie in angezeigt wird der **neues Projekt** Dialogfeld. |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, die Vorlagen-ID. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, die Kennung der Vorlage. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt einen Wert an, die zum Anordnen von gegenüber anderen Vorlagen in der gleichen Kategorie, der Vorlage verwendet wird, entsprechend der Anzeige in einem der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld. |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob ein enthaltender Ordner bei der Instanziierung des Projekts erstellt wird. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt den Namen, den das Projektsystem von Visual Studio generiert wird, wird für das Projekt oder Element an, bei der Erstellung. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob das Visual Studio-Projektsystem den Standardnamen für ein Projekt oder Element generiert wird, wenn es erstellt wird. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob das Projekt als temporäres Projekt erstellt werden kann. |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob die **Durchsuchen** Schaltfläche ist verfügbar in der **neues Projekt** Dialogfeld, damit Benutzer können leicht ändern, das Standardverzeichnis, in dem ein neues Projekt gespeichert ist. |
| [Ausgeblendet](../extensibility/hidden-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob die Vorlage angezeigt, entweder in wird der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld. |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt die Anzahl der übergeordneten Kategorien, die die Vorlage in anzeigen, wird die **neues Projekt** Dialogfeld. |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Optionales Element. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Optionales Element.<br /><br /> Gibt an, ob der **Speicherort** Textfeld in der **neues Projekt** im Dialogfeld entweder aktiviert, deaktiviert oder für die Projektvorlage ausgeblendet ist. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Verwenden Sie dieses Element aus, wenn die Vorlage nur eine bestimmte mindestens erforderliche Version und höhere Versionen, sofern vorhanden, von .NET Framework unterstützt. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob die Vorlage eine Masterseite für Webprojekte unterstützt. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob die Vorlage für Webprojekte codetrennung und das Code-Behind-Seitenmodell unterstützt. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob die Vorlage für mehrere Sprachen identisch ist, und ob die **Sprache** Option steht in der **neues Projekt** Dialogfeld. |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt die Plattform an, auf die die Projektvorlage abzielt. Dieses Element gibt an, dass eine Projektvorlage zum Erstellen [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] apps. |
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Enthält alle Metadaten für die Projektvorlage, Item-Vorlage oder Starterkits.|  
  
## <a name="remarks"></a>Hinweise  
 `TemplateData` ist ein erforderliches Element.  
  
 Wenn Sie nicht über ein optionales Element beinhalten, ist der Standardwert für dieses Element verwendet.  
  
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
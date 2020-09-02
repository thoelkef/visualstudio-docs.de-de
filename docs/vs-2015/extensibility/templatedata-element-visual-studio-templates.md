---
title: TemplateData-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 209d8066d232c63364a045aee6b8dd2153033666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186444"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|[Name](../extensibility/name-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Namen der Vorlage an, wie Sie im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
|[Beschreibung](../extensibility/description-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt die Beschreibung der Vorlage an, wie Sie im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
|[Icon](../extensibility/icon-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Pfad und den Dateinamen der Bilddatei an, die als Symbol dient, das im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** für die Vorlage angezeigt wird.|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Projektvorlage, sodass Sie im Dialogfeld **Neues Projekt** unter der angegebenen Gruppe angezeigt wird.|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Klassifiziert die Projektvorlage, sodass Sie im Dialogfeld **Neues Projekt** unter der angegebenen Unterkategorie angezeigt wird.|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die Vorlagen-ID an.|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die Vorlagen Gruppen-ID an.|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt einen Wert an, der verwendet wird, um die Vorlage neben anderen Vorlagen in derselben Kategorie anzuordnen, wie Sie im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob ein enthaltender Ordner bei der Instanziierung des Projekts erstellt wird.|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt den Namen an, den das Visual Studio-Projekt System für das Projekt oder Element generiert, wenn es erstellt wird.|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob das Visual Studio-Projekt System den Standardnamen für ein Projekt oder Element generiert, wenn es erstellt wird.|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob das Projekt als temporäres Projekt erstellt werden kann.|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob die Schaltfläche " **Durchsuchen** " im Dialogfeld " **Neues Projekt** " verfügbar ist, sodass Benutzer das Standardverzeichnis, in dem ein neues Projekt gespeichert wird, leicht ändern können.|  
|[Hidden](../extensibility/hidden-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob die Vorlage im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die Anzahl der übergeordneten Kategorien an, in denen die Vorlage im Dialogfeld **Neues Projekt** angezeigt wird.|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|Optionales Element.|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|Optionales Element.<br /><br /> Gibt an, ob das Textfeld **Speicherort** im Dialogfeld **Neues Projekt** für die Projektvorlage aktiviert, deaktiviert oder ausgeblendet ist.|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Verwenden Sie dieses Element, wenn die Vorlage nur eine bestimmte Mindestversion und spätere Versionen der .NET Framework unterstützt.|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob die Vorlage eine Master Seite für Webprojekte unterstützt.|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob die Vorlage Code Trennung oder das Code-Behind-Seiten Modell für Webprojekte unterstützt.|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob die Vorlage für mehrere Sprachen identisch ist und ob die **sprach** Option im Dialogfeld **Neues Projekt** verfügbar ist.|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die Plattform an, auf die die Projektvorlage abzielt. Dieses Element gibt an, dass eine Projektvorlage zum Erstellen von-apps verwendet wird [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] .|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Enthält alle Metadaten für die Projektvorlage, die Element Vorlage oder Starter Kit.|  
  
## <a name="remarks"></a>Bemerkungen  
 `TemplateData` ist ein erforderliches Element.  
  
 Wenn Sie kein optionales Element einschließen, wird der Standardwert für dieses Element verwendet.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Anwendung veranschaulicht.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)

---
title: "TemplateData-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData"
helpviewer_keywords: 
  - "TemplateData-Element [Visual Studio-Projektvorlagen]"
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# TemplateData-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.  
  
## Syntax  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Name](../extensibility/name-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Namen der Vorlage an, so wie er im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
|[Description](../extensibility/description-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt die Beschreibung der Vorlage an, so wie sie im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
|[Symbol](../extensibility/icon-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Pfad und den Dateinamen der Bilddatei an, die als Symbol dient, das in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** für die Vorlage angezeigt wird.|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Projektvorlage, sodass sie im Dialogfeld **Neues Projekt** unter der angegebenen Gruppe angezeigt wird.|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Klassifiziert die Projektvorlage, sodass sie im Dialogfeld **Neues Projekt** unter der angegebenen Unterkategorie angezeigt wird.|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die Vorlagen\-ID an.|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die Vorlagengruppen\-ID an.|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt einen Wert an, der die Anordnung der Vorlage unter anderen Vorlagen in derselben Kategorie bestimmt, wenn die Vorlage in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob ein enthaltender Ordner bei der Instanziierung des Projekts erstellt wird.|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt den Namen an, der vom Visual Studio\-Projektsystem bei der Projekt\- oder Elementerstellung generiert wird.|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob der Standardname für ein Projekt oder Element bei der Erstellung vom Visual Studio\-Projektsystem generiert wird.|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob das Projekt als temporäres Projekt erstellt werden kann.|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob die Schaltfläche **Durchsuchen** im Dialogfeld **Neues Projekt** verfügbar ist, sodass Benutzer das Standardverzeichnis problemlos ändern können, in dem ein neues Projekt gespeichert wird.|  
|[Hidden](../extensibility/hidden-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob die Vorlage in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die Anzahl von übergeordneten Kategorien an, von denen die Vorlage im Dialogfeld **Neues Projekt** angezeigt wird.|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|Optionales Element.|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|Optionales Element.<br /><br /> Gibt an, ob das Textfeld **Speicherort** im Dialogfeld **Neues Projekt** für die Projektvorlage aktiviert, deaktiviert oder ausgeblendet ist.|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Verwenden Sie dieses Element, wenn die Vorlage nur eine bestimmte minimale Version und höhere Versionen, sofern zutreffend, von .NET Framework unterstützt.|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob die Vorlage eine Masterseite für Webprojekte unterstützt.|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob die Vorlage die Codetrennung oder das Code\-Behind\-Seitenmodell für Webprojekte unterstützt.|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, ob die Vorlage für mehrere Programmiersprachen identisch ist und ob im Dialogfeld **Neues Projekt** die Option **Sprache** verfügbar ist.|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die diese Plattform die Projektvorlagenziele an.  Dieses Element gibt an, dass eine Projektvorlage verwendet wird, um [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] App zu erstellen.|  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Enthält alle Metadaten für die Projektvorlage, Elementvorlage oder das Starter Kit.|  
  
## Hinweise  
 `TemplateData` ist ein erforderliches Element.  
  
 Wenn Sie kein optionales Element einschließen, wird der Standardwert für dieses Element verwendet.  
  
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
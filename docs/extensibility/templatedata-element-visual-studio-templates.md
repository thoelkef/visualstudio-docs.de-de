---
title: TemplateData-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699197"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData-Element (Visual Studio-Vorlagen)
Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.

 \<VSTemplate \<> TemplateData>

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
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

| Element | BESCHREIBUNG |
| - | - |
| [Name](../extensibility/name-element-visual-studio-templates.md) | Erforderliches Element<br /><br /> Gibt den Namen der Vorlage an, wie sie entweder im Dialogfeld **Neues Projekt** oder im Dialogfeld Neues **Element hinzufügen** angezeigt wird. |
| [Beschreibung](../extensibility/description-element-visual-studio-templates.md) | Erforderliches Element<br /><br /> Gibt die Beschreibung der Vorlage an, wie sie entweder im Dialogfeld **Neues Projekt** oder im Dialogfeld Neues **Element hinzufügen** angezeigt wird. |
| [Symbol](../extensibility/icon-element-visual-studio-templates.md) | Erforderliches Element<br /><br /> Gibt den Pfad und den Dateinamen der Bilddatei an, die als Symbol dient, das entweder im Dialogfeld **Neues Projekt** oder im Dialogfeld Neues **Element hinzufügen** für die Vorlage angezeigt wird. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Erforderliches Element<br /><br /> Kategorisiert die Projektvorlage so, dass sie unter der angegebenen Gruppe im Dialogfeld **Neues Projekt** angezeigt wird. |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Klassifiziert die Projektvorlage so, dass sie unter der angegebenen Unterkategorie im Dialogfeld **Neues Projekt** angezeigt wird. |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt die Vorlagen-ID an. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt die Vorlagengruppen-ID an. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt einen Wert an, der zum Anordnen der Vorlage unter anderen Vorlagen in derselben Kategorie verwendet wird, wie er im Dialogfeld **Neues Projekt** oder Neues **Element hinzufügen** angezeigt wird. |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob bei der Instanziierung des Projekts ein enthaltender Ordner erstellt wird. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt den Namen an, den das Visual Studio-Projektsystem für das Projekt oder Element generiert, wenn es erstellt wird. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob das Visual Studio-Projektsystem den Standardnamen für ein Projekt oder Element generiert, wenn es erstellt wird. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob das Projekt als temporäres Projekt erstellt werden kann (nur Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob die **Schaltfläche Durchsuchen** im Dialogfeld **Neues Projekt** verfügbar ist, damit Benutzer das Standardverzeichnis, in dem ein neues Projekt gespeichert wird, problemlos ändern können. |
| [Versteckte](../extensibility/hidden-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob die Vorlage entweder im Dialogfeld **Neues Projekt** oder Im Dialogfeld Neues **Element hinzufügen** angezeigt wird. |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt die Anzahl der übergeordneten Kategorien an, die die Vorlage im Dialogfeld **Neues Projekt** anzeigen. |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Optionales Element. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Optionales Element.<br /><br /> Gibt an, ob das Textfeld **Standort** im Dialogfeld **Neues Projekt** für die Projektvorlage aktiviert, deaktiviert oder ausgeblendet ist. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Verwenden Sie dieses Element, wenn die Vorlage nur eine bestimmte Mindestversion und ggf. eine neuere Version von .NET Framework unterstützt. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob die Vorlage eine Masterseite für Webprojekte unterstützt. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob die Vorlage die Codetrennung oder das CodeBehind-Seitenmodell für Webprojekte unterstützt. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt an, ob die Vorlage für mehrere Sprachen identisch ist und ob die Option **Sprache** im Dialogfeld **Neues Projekt** verfügbar ist. |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Optionales Element.<br /><br /> Gibt die Plattform an, auf die die Projektvorlage abzielt. Dieses Element gibt an, dass eine [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Projektvorlage zum Erstellen von Apps verwendet wird. |

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Enthält alle Metadaten für die Projektvorlage, Elementvorlage oder das Startkit.|

## <a name="remarks"></a>Bemerkungen
 `TemplateData`ist ein erforderliches Element.

 Wenn Sie kein optionales Element einschließen, wird der Standardwert für dieses Element verwendet.

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

## <a name="see-also"></a>Weitere Informationen
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)

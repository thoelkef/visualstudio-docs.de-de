---
title: EnableLocationBrowseButton-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2be2f67d08fcac39d26f9a27f76ad8aff967440b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334465"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton-Element (Visual Studio-Vorlagen)
Gibt an, ob die **Durchsuchen** Schaltfläche ist verfügbar in der **neues Projekt** Dialogfeld, damit Benutzer können leicht ändern, das Standardverzeichnis, in dem ein neues Projekt gespeichert ist.

 \<VSTemplate> \<TemplateData> \<EnableLocationBrowseButton>

## <a name="syntax"></a>Syntax

```
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text muss entweder `true` oder `false`, der angibt, ob zum Anzeigen der **Durchsuchen** Schaltfläche der **neues Projekt** Dialogfeld.

## <a name="remarks"></a>Hinweise
 `EnableLocationBrowseButton` ist ein optionales Element. Der Standardwert ist `true`, welche zeigt die **Durchsuchen** Schaltfläche der **neues Projekt** Dialogfeld.

 In der **neues Projekt** im Dialogfeld die **Speicherort** Textfeld gibt das Verzeichnis, in dem ein neues Projekt gespeichert ist. Die **Durchsuchen** Schaltfläche können Sie dieses Verzeichnis zu ändern, indem Sie die Anzeige der **Projektspeicherort** Dialogfeld können Sie leicht zu einem anderen Verzeichnis zu navigieren, die von Ihrem Computer verfügbar ist, und Wählen Sie sie, wie das Verzeichnis, in dem das neue Projekt gespeichert ist.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für eine Windows-Anwendung in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
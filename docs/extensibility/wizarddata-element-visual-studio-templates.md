---
title: WizardData-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3f9d2e971d944b964f4b194d1324ff960fbd24
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740390"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData-Element (Visual Studio-Vorlagen)

Gibt benutzerdefinierte XML-Xml-Code an

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>Syntax

```xml
<WizardData>
    <!-- XML to pass to the custom wizard extension -->
    ...
</WizardData>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Enthält alle Metadaten für die Projektvorlage, Elementvorlage oder das Startkit.|

## <a name="text-value"></a>Textwert

Ein Textwert ist optional.

Dieser Text gibt den benutzerdefinierten XML-Code an, der an die benutzerdefinierte Assistentenerweiterung übergeben werden soll, die im [WizardExtension-Element](../extensibility/wizardextension-element-visual-studio-templates.md) angegeben ist.

## <a name="remarks"></a>Bemerkungen

In diesem Element kann jeder XML-Code angegeben werden. Der XML-Code wird als Parameter an die benutzerdefinierte Assistentenerweiterung übergeben, sodass die Erweiterung den Inhalt dieses Elements verwenden kann. Für diese Daten wird keine Validierung durchgeführt.

Der Inhalt des **WizardData-Elements** wird unverändert als Parameter innerhalb des Zeichenfolgenwörterbuchs der Parameter in der `IWizard.RunStarted` Methode übergeben. Der Wörterbuchschlüssel `$wizarddata$`heißt .

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden die Metadaten für die Standardprojektvorlage für eine Windows-Anwendung von C-Windows veranschaulicht.

```xml
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
    <WizardData>
        <!-- XML to pass to the custom wizard extension -->
    </WizardData>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen

- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [WizardExtension-Element (Visual Studio-Vorlagen)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)

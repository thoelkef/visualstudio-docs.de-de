---
title: MaxFrameworkVersion-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702622"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion-Element (Visual Studio-Vorlagen)

Gibt die maximale Version von .NET Framework an, die für die Vorlage erforderlich ist. Er bestimmt den höchsten verfügbaren Wert in der Dropdownliste **Zielframeworkversion** des Dialogfelds **Neues Projekt.** Damit Benutzer eine Frameworkversion auswählen können, müssen Sie [requiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) auch als Mindestversion von .NET Framework für die Vorlage angeben.

> [!IMPORTANT]
> Ab Visual Studio 2017 Version 15.6 ist die Dropdownliste **Zielframeworkversion** kein Filter mehr für angezeigte Vorlagen im Abschnitt **Vorlagen** des Dialogfelds **Neues Projekt.** Stattdessen fungiert die Dropdown-Liste **Zielframeworkversion** als Frameworkauswahl für die ausgewählte Vorlage.

 \<VSTemplate \<> TemplateData> \<MaxFrameworkVersion>

## <a name="syntax"></a>Syntax

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Kategorisiert die Vorlage und definiert, wie sie entweder im Dialogfeld **Neues Projekt** oder im Dialogfeld Neues **Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text muss die höchste Versionsnummer von .NET Framework sein, die von der Vorlage zugelassen wird.

## <a name="remarks"></a>Bemerkungen

`MaxFrameworkVersion` ist ein optionales Element. Das `MaxFrameworkVersion` Element sollte weggelassen werden, es sei denn, es ist erforderlich, um den unterstützten Bereich von .NET Framework-Versionen für die Vorlage nicht versehentlich einzuschränken. Sie sollte auch weggelassen werden, wenn .NET Framework nicht auf die Vorlage anwendbar ist.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden die [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Metadaten für eine Standardklassenvorlage veranschaulicht.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

In diesem Beispiel ist die maximale Version von .NET Framework, `MaxFrameworkVersion`die für die Vorlage erforderlich ist, dargestellt durch , 4.7.1. Ein mit dieser Vorlage erstelltes Projekt kann auf .NET Framework-Versionen bis 4.7.1 abzielen.

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)

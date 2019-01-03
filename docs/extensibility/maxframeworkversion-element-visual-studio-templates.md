---
title: MaxFrameworkVersion-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e28364360cf636273384480a35cd07468b9b7e6f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845576"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion-Element (Visual Studio-Vorlagen)

Gibt die maximale Version von .NET Framework, die von der Vorlage erforderlich sind. Bestimmt den höchsten Wert, der zur Verfügung, in der **Zielframeworkversion** Dropdown-Menü des der **neues Projekt** Dialogfeld. Sie müssen auch angeben, damit Benutzer eine Framework-Version auswählen können, [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) als die Mindestversion von .NET Framework für die Vorlage.

> [!IMPORTANT]
> Ab Visual Studio 2017 Version 15.6, die **Framework-Zielversion** Dropdown ist nicht mehr als einen Filter für die angezeigten Vorlagen in die **Vorlagen** Teil der **neues Projekt** Dialogfeld. Stattdessen die **Zielframeworkversion** Dropdownliste fungiert als eine Framework-Auswahl für die ausgewählte Vorlage.

 \<VSTemplate > \<TemplateData > \<MaxFrameworkVersion >

## <a name="syntax"></a>Syntax

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie es angezeigt wird, entweder in der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text muss die höchste Versionsnummer von .NET Framework, die von der Vorlage zulässig ist.

## <a name="remarks"></a>Hinweise

`MaxFrameworkVersion` ist ein optionales Element. Die `MaxFrameworkVersion` Element sollte ausgelassen werden, es sei denn, es erforderlich, damit nicht versehentlich die unterstützten Bereich von .NET Framework-Versionen für die Vorlage beschränkt ist. Es sollte auch weggelassen werden, wenn .NET Framework nicht auf die Vorlage anwendbar ist.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Metadaten für die Standard [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] -Klassenvorlage.

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

In diesem Beispiel ist die maximale Version des .NET Framework, die von der Vorlage erforderlich ist, der durch dargestellt `MaxFrameworkVersion`, 4.7.1 ist. Ein Projekt mit dieser Vorlage erstellt wurde, kann .NET Framework-Versionen bis 4.7.1 abzielen.

## <a name="see-also"></a>Siehe auch

- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)

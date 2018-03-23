---
title: MaxFrameworkVersion-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: edc3f443423a6c70815c4f32f1b2c91d5ead85b6
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion-Element (Visual Studio-Vorlagen)

Gibt die maximale Version von .NET Framework, die von der Vorlage erforderlich ist. Bestimmt den höchsten Wert zur Verfügung, in der **Zielframeworkversion** der Dropdownliste die **neues Projekt** Dialogfeld. Sie müssen auch angeben, damit Benutzer eine Framework-Version auswählen können, [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) als die Mindestversion von .NET Framework für die Vorlage.

> [!IMPORTANT]
> Ab Visual Studio 2017 Version 15,6, die **Zielframeworkversion** Dropdownliste ist nicht mehr als einen Filter für die angezeigten Vorlagen in die **Vorlagen** Teil der **neues Projekt** Dialogfeld. Stattdessen die **Zielframeworkversion** Dropdownliste fungiert als ein Framework Auswahl für die ausgewählte Vorlage.

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie er angezeigt wird, entweder in der **neues Projekt** oder **neues Element hinzufügen** (Dialogfeld).|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text muss die höchste Versionsnummer von .NET Framework, die die Vorlage nicht zulässig ist.

## <a name="remarks"></a>Hinweise

`MaxFrameworkVersion` ist ein optionales Element. Die `MaxFrameworkVersion` Element sollte weggelassen werden, nur bei Bedarf, damit nicht versehentlich unterstützten Bereich von .NET Framework-Versionen für die Vorlage zu beschränken. Es sollte auch weggelassen werden, wenn .NET Framework nicht auf die Vorlage anwendbar ist.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Metadaten für einen Standard [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Klassenvorlage.

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

In diesem Beispiel die maximale Version des .NET Framework, die von der Vorlage erforderlich ist, die durch dargestellt `MaxFrameworkVersion`, 4.7.1 ist. Ein mit dieser Vorlage erstelltes Projekt kann .NET Framework-Versionen bis 4.7.1 abzielen.

## <a name="see-also"></a>Siehe auch

- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)

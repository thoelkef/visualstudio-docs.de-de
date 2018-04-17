---
title: RequiredFrameworkVersion-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adc1a138c50c0fe13962f6601449eb3498d90398
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion-Element (Visual Studio-Vorlagen)

Gibt die Mindestversion von .NET Framework, die von der Vorlage erforderlich ist. Es bewirkt, dass die **Zielframeworkversion** Dropdownliste angezeigt werden die **neues Projekt** Dialogfeld. Die `RequiredFrameworkVersion` Element bestimmt außerdem den niedrigsten Wert in der Dropdownliste verfügbar.

> [!IMPORTANT]
> Ab Visual Studio 2017 Version 15,6, die **Zielframeworkversion** Dropdownliste ist nicht mehr als einen Filter für die angezeigten Vorlagen in die **Vorlagen** Teil der **neues Projekt** Dialogfeld. Stattdessen fungiert die Dropdownliste als ein Framework Auswahl für die ausgewählte Vorlage.

 \<VSTemplate > \<TemplateData > \<RequiredFrameworkVersion >

## <a name="syntax"></a>Syntax

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Der Text muss die minimale Versionsnummer von .NET Framework, die für die Vorlage erforderlich ist.

## <a name="remarks"></a>Hinweise

`RequiredFrameworkVersion` ist ein optionales Element. Verwenden Sie dieses Element nur dann, wenn die Vorlage für eine bestimmte mindestens erforderliche Version (und höher, sofern vorhanden) unterstützt von .NET Framework. Bei Angabe der `RequiredFrameworkVersion` Element und die Vorlage für eine bestimmte mindestens erforderliche Version von .NET Framework unterstützt keine der **Zielframeworkversion** Dropdownliste wird angezeigt, wenn sie nicht anwendbar ist.

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

In diesem Beispiel die Mindestversion von .NET Framework, die von der Vorlage erforderlich ist, die durch dargestellt `RequiredFrameworkVersion`, 3.0 ist. Ein mit dieser Vorlage erstelltes Projekt kann .NET Framework-Versionen 3.0 beginnend abzielen.

## <a name="see-also"></a>Siehe auch

- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Festlegen einer bestimmten .NET-Framework-Version](../ide/targeting-a-specific-dotnet-framework-version.md)

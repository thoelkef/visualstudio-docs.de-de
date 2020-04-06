---
title: RequiredFrameworkVersion-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701502"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion-Element (Visual Studio-Vorlagen)

Gibt die Mindestversion von .NET Framework an, die für die Vorlage erforderlich ist. Dadurch wird die Dropdown-Liste **Zielframeworkversion** im Dialogfeld **Neues Projekt** angezeigt. Das `RequiredFrameworkVersion` Element bestimmt auch den niedrigsten in der Dropdown-Liste verfügbaren Wert.

> [!IMPORTANT]
> Ab Visual Studio 2017 Version 15.6 ist die Dropdownliste **Zielframeworkversion** kein Filter mehr für angezeigte Vorlagen im Abschnitt **Vorlagen** des Dialogfelds **Neues Projekt.** Stattdessen fungiert die Dropdown-Liste als Frameworkauswahl für die ausgewählte Vorlage.

 \<VSTemplate \<> TemplateData> \<RequiredFrameworkVersion>

## <a name="syntax"></a>Syntax

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Der Text muss die Mindestversionsnummer von .NET Framework sein, die für die Vorlage erforderlich ist.

## <a name="remarks"></a>Bemerkungen

`RequiredFrameworkVersion` ist ein optionales Element. Verwenden Sie dieses Element nur, wenn die Vorlage eine bestimmte Mindestversion (und ggf. spätere Versionen) von .NET Framework unterstützt. Wenn Sie `RequiredFrameworkVersion` das Element angeben und Ihre Vorlage keine bestimmte Mindestversion von .NET Framework unterstützt, wird die Dropdown-Liste **Target Framework Version** angezeigt, wenn sie nicht anwendbar ist.

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

In diesem Beispiel ist die Mindestversion von .NET Framework, `RequiredFrameworkVersion`die für die Vorlage erforderlich ist, dargestellt durch , 3.0. Ein mit dieser Vorlage erstelltes Projekt kann auf .NET Framework-Versionen ab 3.0 abzielen.

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Übersicht über Frameworkziele](../ide/visual-studio-multi-targeting-overview.md)

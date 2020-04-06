---
title: SortOrder-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 935d00335a21d3e129e79ce351e554ea93787447
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699953"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder-Element (Visual Studio-Vorlagen)
Gibt einen Wert an, der zum Anordnen der Vorlage unter anderen Vorlagen in derselben Kategorie verwendet wird, wie er im Dialogfeld **Neues Projekt** oder Neues **Element hinzufügen** angezeigt wird.

 \<VSTemplate \<> TemplateData> \<SortOrder>

## <a name="syntax"></a>Syntax

```
<SortOrder> ... </SortOrder>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Ein, `integer` der den Sortierauftragswert darstellt.

## <a name="remarks"></a>Bemerkungen
 `SortOrder` ist ein optionales Element. Der Standardwert ist 100, und alle Werte müssen ein Vielfaches von 10 sein.

 Das `SortOrder` Element wird für vom Benutzer erstellte Vorlagen ignoriert. Alle vom Benutzer erstellten Vorlagen werden alphabetisch sortiert.

 Vorlagen mit niedrigen Sortierreihenfolgewerten werden entweder im Dialogfeld **Neues Projekt** oder Neues **Element hinzufügen** vor Vorlagen mit hohen Sortierreihenfolgewerten angezeigt.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Metadaten für eine Standardklassenvorlage veranschaulicht.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 In diesem Beispiel `SortOrder` ist das Element relativ hoch. Es [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ist wahrscheinlich, dass andere `SortOrder` Elementvorlagen `290` einen niedrigeren Wert als diese Vorlage im Dialogfeld **Neues Element** haben und vor dieser Vorlage angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)

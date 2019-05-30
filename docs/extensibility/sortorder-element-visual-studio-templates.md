---
title: SortOrder-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edab3547a16f32f3a8177b3efa7a342c4aae5955
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331847"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder-Element (Visual Studio-Vorlagen)
Gibt einen Wert an, die zum Anordnen von gegenüber anderen Vorlagen in der gleichen Kategorie, der Vorlage verwendet wird, entsprechend der Anzeige in einem der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld.

 \<VSTemplate> \<TemplateData> \<SortOrder>

## <a name="syntax"></a>Syntax

```
<SortOrder> ... </SortOrder>
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

 Ein `integer` , das den Sortierreihenfolgenwert darstellt.

## <a name="remarks"></a>Hinweise
 `SortOrder` ist ein optionales Element. Der Standardwert ist 100, und alle Werte müssen ein Vielfaches von 10 sein.

 Die `SortOrder` Element wird für benutzerdefinierte Vorlagen ignoriert. Alle Benutzer erstellte Vorlagen sind alphabetisch sortiert.

 Vorlagen mit niedrigen Sortierwerte angezeigt werden, entweder in der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld vor dem Vorlagen, die hohe Sortierwerte enthalten.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Metadaten für die Standard [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] -Klassenvorlage.

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

 In diesem Beispiel die `SortOrder` Element ist relativ hoch. Ist es wahrscheinlich, dass andere [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Elementvorlagen müssen eine `SortOrder` Werts kleiner als `290` und wird angezeigt, bevor Sie diese Vorlage in der **neues Element** Dialogfeld.

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
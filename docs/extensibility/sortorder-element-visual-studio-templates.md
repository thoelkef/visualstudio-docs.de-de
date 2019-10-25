---
title: Sortor der-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719926"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder-Element (Visual Studio-Vorlagen)
Gibt einen Wert an, der verwendet wird, um die Vorlage neben anderen Vorlagen in derselben Kategorie anzuordnen, wie Sie im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.

 \<VSTemplate > \<TemplateData > \<SortOrder >

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

 Ein-`integer`, der den Sortierreihen folgen Wert darstellt.

## <a name="remarks"></a>Hinweise
 `SortOrder` ist ein optionales Element. Der Standardwert ist 100, und alle Werte müssen ein Vielfaches von 10 sein.

 Das `SortOrder`-Element wird für vom Benutzer erstellte Vorlagen ignoriert. Alle vom Benutzer erstellten Vorlagen sind alphabetisch sortiert.

 Vorlagen mit niedrigen Sortierreihenfolge-Werten werden im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** vor Vorlagen mit Werten für hohe Sortierreihenfolge angezeigt.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für eine Standard-[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Klassen Vorlage veranschaulicht.

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

 In diesem Beispiel ist das `SortOrder` Element relativ hoch. Es ist wahrscheinlich, dass andere Vorlagen für [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Elemente einen `SortOrder` Wert aufweisen, der kleiner als `290` ist und vor dieser Vorlage im Dialogfeld **Neues Element** angezeigt wird.

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
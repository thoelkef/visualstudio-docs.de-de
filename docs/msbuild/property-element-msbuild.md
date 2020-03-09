---
title: Property-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e50a6dd66c2dca7fa4159c578ccd334ed1d26cae
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632952"
---
# <a name="property-element-msbuild"></a>Property-Element (MSBuild)

Enthält einen benutzerdefinierten Eigenschaftennamen und -wert. Jede Eigenschaft, die in einem MSBuild-Projekt verwendet wird, muss als untergeordnetes Element eines `PropertyGroup`-Elements angegeben werden.

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Syntax

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|

### <a name="child-elements"></a>Untergeordnete Elemente

 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Grouping-Element für Eigenschaften.|

## <a name="text-value"></a>Textwert

 Ein Textwert ist optional.

 Dieser Text gibt den Eigenschaftswert an und enthält möglicherweise XML.

## <a name="remarks"></a>Hinweise

 Eigenschaftennamen sind auf ASCII-Zeichen beschränkt. Im Projekt wird durch die Platzierung der Eigenschaftenname zwischen „`$(`“ und „`)`“ verwiesen werden. Beispielsweise würde `$(builddir)\classes` in *build\classes* aufgelöst, wenn die `builddir`-Eigenschaft den Wert `build` hat. Weitere Informationen zu Eigenschaften finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

## <a name="example"></a>Beispiel

 Im folgenden Code wird die `Optimization`-Eigenschaft auf `false` und die `DefaultVersion`-Eigenschaft auf `1.0` festgelegt, wenn die `Version`-Eigenschaft leer ist.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Siehe auch

- [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md)
- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)

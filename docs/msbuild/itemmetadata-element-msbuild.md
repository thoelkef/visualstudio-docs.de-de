---
title: ItemMetadata-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18e1722fcd6867ca5e8ae52e220ff0a3dd2a3b7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633615"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata-Element (MSBuild)

Enthält einen benutzerdefinierten Elementmetadatenschlüssel, der den Elementmetadatenwert enthält. Ein Element kann über eine beliebige Anzahl von Metadaten-Schlüssel-Wert-Paaren verfügen.

 \<Project> \<ItemGroup> \<Item>

## <a name="syntax"></a>Syntax

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions (Bedingungen)](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Ein benutzerdefiniertes Element, das die Eingaben für den Buildprozess definiert.|

## <a name="text-value"></a>Textwert

 Ein Textwert ist optional.

 Dieser Text legt den Elementmetadatenwert fest, der im Text- oder XML-Format vorhanden sein kann.

## <a name="example"></a>Beispiel

 Das folgende Codebeispiel veranschaulicht das Hinzufügen von `Culture`-Metadaten mit dem Wert `fr` zum Element `CSFile`.

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>Weitere Informationen

- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
- [Elemente](../msbuild/msbuild-items.md)

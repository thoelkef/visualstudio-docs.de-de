---
title: Bedingte Attribute des vsct-XML-Schemas | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2b1fb3ee1b2cd396f25ec5591a585f8d87648d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697943"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Bedingte Attribute des vsct-XML-Schemas
Sie können bedingte Attribute auf alle Listen und Elemente anwenden. Logische Operatoren und Symbol Erweiterungs Ausdrücke werden als true oder false ausgewertet. True gibt an, dass die zugeordnete Liste oder das zugehörige Element in der resultierenden Ausgabe enthalten ist.

 Sie können tokenerweiterungen für andere tokenerweiterungen oder Konstanten testen. Die-Funktion `Defined()` testet, ob ein bestimmter Name definiert wurde, auch wenn Sie über keinen Wert verfügt.

 Wenn ein Condition-Attribut auf eine Liste angewendet wird, wird die Bedingung auf jedes untergeordnete Element in der Liste angewendet. Wenn ein untergeordnetes Element selbst ein Condition-Attribut enthält, wird die Bedingung mit dem übergeordneten Ausdruck durch eine and-Operation kombiniert.

 Die Werte 1, "1" und "true" werden als "true" ausgewertet, und 0, "0" und "false" werden als "false" ausgewertet.

## <a name="operators"></a>Operatoren
 Verwenden Sie die folgenden Operatoren, um bedingte Ausdrücke auszuwerten.

|Operator|Definition|
|--------------|----------------|
|(,)|Gruppierung|
|!|Logisches Nicht|
|\<, >, \<=, >=, ==, !=|Relation und Gleichheit|
|und|Boolean|
|oder|Boolean|

## <a name="examples"></a>Beispiele

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehls Tabelle (. Vsct-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

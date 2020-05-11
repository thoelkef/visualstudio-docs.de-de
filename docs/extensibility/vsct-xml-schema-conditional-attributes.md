---
title: VSCT XML-Schema Bedingte Attribute | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697943"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>BEDINGTE VSCT-XML-Schema-Schemaattribute
Sie können bedingte Attribute auf alle Listen und Elemente anwenden. Logische Operatoren und Symbolerweiterungsausdrücke werden als true oder false ausgewertet. Wenn true, wird die zugeordnete Liste oder das zugeordnete Element in die resultierende Ausgabe einbezogen.

 Sie können Tokenerweiterungen mit anderen Tokenerweiterungen oder Konstanten testen. Die `Defined()` Funktion testet, ob ein bestimmter Name definiert wurde, auch wenn er keinen Wert hat.

 Wenn ein Condition-Attribut auf eine Liste angewendet wird, wird die Bedingung auf jedes untergeordnete Element in der Liste angewendet. Wenn ein untergeordnetes Element selbst ein Condition-Attribut enthält, wird seine Bedingung durch einen AND-Vorgang mit dem übergeordneten Ausdruck kombiniert.

 Die Werte 1, '1' und 'true' werden als wahr ausgewertet, und 0, '0' und 'false' werden als false ausgewertet.

## <a name="operators"></a>Operatoren
 Verwenden Sie die folgenden Operatoren, um bedingte Ausdrücke auszuwerten.

|Operator|Definition|
|--------------|----------------|
|(,)|Gruppierung|
|!|Logisches Nicht|
|\<, >, \<=, >=, ==, !=|Relation und Gleichheit|
|and|Boolean|
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
- [Visual Studio-Befehlstabelle (. Vsct)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

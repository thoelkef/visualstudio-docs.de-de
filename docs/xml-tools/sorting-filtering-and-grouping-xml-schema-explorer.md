---
title: Sortieren, Filtern und Gruppieren im XML-Schema-Explorer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd288171cd8713e6b403f71a4eee6ba09d3f6ea9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592515"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sortieren, Filtern und gruppieren (XML-Schema-Explorer)

In diesem Thema werden die Optionen beschrieben, die über das Menü **Sortieren, Filtern und Gruppieren von Optionen** auf der Symbolleiste des **XML-Schema-Explorers** verfügbar sind.

## <a name="filter-options"></a>Filteroptionen

Die folgenden Filteroptionen sind verfügbar. Standardmäßig sind die Optionen **Namespaces anzeigen** und **Schema Dateien anzeigen** ausgewählt.

- **Namespaces anzeigen**.

- **Schema Dateien anzeigen**.

- **Compositors anzeigen (Sequence/Choice/all)** .

## <a name="sorting-options"></a>Sortieroptionen

Die folgenden Sortierungsoptionen sind verfügbar. Der Standardwert ist **nach Typ sortieren**. Die Option " **Sortieren nach** " gilt nicht für Dateien und Namespaces.

- **Nach Typ sortieren**.

- **Nach Namen sortieren**.

- **Dokument Reihenfolge**.

### <a name="sort-by-type"></a>Nach Typ sortieren

Wenn die Option **nach Typ sortieren** ausgewählt ist, werden globale Knoten in der folgenden Reihenfolge sortiert. Knoten sind innerhalb jeder Gruppe alphabetisch sortiert.

1. `import`-Knoten

2. `include`-Knoten

3. `redefine`-Knoten

4. `attribute`-Knoten

5. `attributeGroup`-Knoten

6. `complexType`-Knoten

7. `simpleType`-Knoten

8. `element`-Knoten

9. `group`-Knoten

### <a name="sort-by-name"></a>Nach Namen sortieren

Wenn die Option **nach Name sortieren** ausgewählt ist, werden globale Knoten in der folgenden Reihenfolge sortiert:

1. `import` Knoten (in alphabetischer Reihenfolge von Namespaces).

2. `include`-Knoten (in alphabetischer Reihenfolge der `schemaLocation`-Attribute)

3. `redefine`-Knoten (in alphabetischer Reihenfolge der `schemaLocation`-Attribute)

4. Andere globale Knoten in alphabetischer Reihenfolge

### <a name="document-order"></a>Dokumentreihenfolge

Die Option **Dokument Reihenfolge** ist verfügbar, wenn die Option **Schema Dateien anzeigen** ausgewählt ist. Wenn die **Dokument Reihenfolge** ausgewählt ist, werden globale Knoten in der Reihenfolge angezeigt, in der Sie in der Schema Datei angezeigt werden.

## <a name="persisting-sortfilter-options"></a>Beibehalten von Sortier-/Filteroptionen

Die Sortierungs-, Filter- und Gruppierungsoptionen werden in der Registrierung für jeden Benutzer gespeichert, unabhängig davon, welche Projektmappe oder welche Dateien beim Ändern der Einstellungen geöffnet waren.

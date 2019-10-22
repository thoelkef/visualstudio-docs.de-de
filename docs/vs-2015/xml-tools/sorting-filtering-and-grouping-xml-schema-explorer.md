---
title: Sortieren, Filtern und gruppieren (XML-Schema-Explorer) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c28842a92ab598ff196e80fc96678c256e4db8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656145"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Sortieren, Filtern und Gruppieren (XML-Schema-Explorer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden die Optionen beschrieben, die über das Menü **Sortieren, Filtern und Gruppieren von Optionen** auf der Symbolleiste des XML-Schema-Explorers verfügbar sind.

## <a name="filter-options"></a>Filteroptionen
 Die folgenden Filteroptionen sind verfügbar. Standardmäßig sind die Optionen **Namespaces anzeigen** und **Schema Dateien anzeigen** ausgewählt.

- **Namespaces anzeigen**.

- **Schema Dateien anzeigen**.

- **Compositors anzeigen (Sequence/Choice/all)** .

## <a name="sorting-options"></a>Sortierungsoptionen
 Die folgenden Sortierungsoptionen sind verfügbar. Der Standardwert ist **nach Typ sortieren**. Die "Sortieren nach"-Optionen gelten nicht für Dateien und Namespaces.

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

1. `import`-Knoten (in alphabetischer Reihenfolge der Namespaces)

2. `include`-Knoten (in alphabetischer Reihenfolge der `schemaLocation`-Attribute)

3. `redefine`-Knoten (in alphabetischer Reihenfolge der `schemaLocation`-Attribute)

4. Andere globale Knoten in alphabetischer Reihenfolge

### <a name="document-order"></a>Dokumentreihenfolge
 Die Option **Dokument Reihenfolge** ist verfügbar, wenn die Option **Schema Dateien anzeigen** ausgewählt ist. Wenn die **Dokument Reihenfolge** ausgewählt ist, werden globale Knoten in der Reihenfolge angezeigt, in der Sie in der Schema Datei angezeigt werden.

## <a name="persisting-sortfilter-options"></a>Speichern von Sortierungs-/Filteroptionen
 Die Sortierungs-, Filter- und Gruppierungsoptionen werden in der Registrierung für jeden Benutzer gespeichert, unabhängig davon, welche Projektmappe oder welche Dateien beim Ändern der Einstellungen geöffnet waren.

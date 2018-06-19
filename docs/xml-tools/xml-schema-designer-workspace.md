---
title: Arbeitsbereich des XML-Schema-Designers
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 588fa495-fe7f-4b16-8a9f-6b6b8d2d502a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 317588e4d6c81a13a18c036a040508a1adebafcb
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2018
ms.locfileid: "34476713"
---
# <a name="xml-schema-designer-workspace"></a>XML-Schema-Designer-Arbeitsbereich

Der XML-Schema-Designer (XSD-Designer) ist ein grafisches Tool, mit dem Sie die XML-Schemas untersuchen können. Zusätzlich zu den [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md), ermöglicht das Durchsuchen und Navigieren in der Struktur der XML-Schema und Suchvorgänge ausführen, der XSD-Designer bietet drei Ansichten, die Sie zur Untersuchung des XSD-Schemas im Detail zu ermöglichen. Die Ausgangsansicht ist der Ausgangspunkt für den XSD-Designer. In dieser Ansicht können Sie zu anderen Ansichten des XSD-Designers navigieren und die Details des Schemasets sehen. Die Diagrammansicht bietet eine Übersicht über ein Schemaset und die Beziehungen zwischen den Schemaknoten. Die Inhaltsmodellansicht bietet eine grafische Darstellung der Details lokaler und globaler Schemaknoten, einschließlich einfacher und komplexer Typen, Elemente, Gruppen, Attribute und Attributgruppen.

Bevor Sie bestimmte Knoten untersuchen können, müssen Sie sie zuerst dem Arbeitsbereich hinzufügen. Der Arbeitsbereich wird für alle Ansichten verwendet.

## <a name="add-nodes-to-the-workspace"></a>Hinzufügen von Knoten zum Arbeitsbereich

Zum Hinzufügen von Knoten zum Arbeitsbereich stehen die folgenden Methoden zur Auswahl:

-   Im Abschnitt "Details zum Schemaset" die [Ausgangsansicht](../xml-tools/start-view.md), klicken Sie auf die **hinzufügen** neben der globalen Knotentyp.

-   Drag & drop verschieben Sie globale Knoten, Dateiknoten und Namespaceknoten aus der **XML-Schema-Explorer** auf eine der drei Ansichten. Weitere Informationen finden Sie im Abschnitt "Ziehen und Ablegen von Knoten" in [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md).

-   Verwenden Sie das Kontextmenü in der **XML-Schema-Explorer**. Weitere Informationen finden Sie unter [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md).

-   Führen Sie eine Suche in der XSD-Explorer, und klicken Sie auf die **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** Schaltfläche im Bereich Zusammenfassung der Ergebnisse. Weitere Informationen finden Sie unter [Durchsuchen des Schemasets](../xml-tools/searching-the-schema-set.md).

## <a name="switch-views"></a>Ansichten wechseln

Zum Wechseln zwischen den Ansichten stehen folgende Methoden zur Auswahl:

-   XSD-Designer-Symbolleiste

-   Kontextmenüs der Inhaltsmodellansicht und Diagrammansicht

-   Wasserzeichen in der Ausgangsansicht oder der leeren Inhaltsmodell- oder Diagrammansicht

-   Hotkeys: **STRG**+**1** für die Ausgangsansicht **STRG**+**2** für die Diagrammansicht und  **STRG**+**3** für die Inhaltsmodellansicht.
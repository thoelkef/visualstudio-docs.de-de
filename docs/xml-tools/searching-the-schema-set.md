---
title: 'XML-Schema-Explorer: Durchsuchen des Schema Satzes'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8378ebaccefaedfcc3d83f23bcab56f7417264dd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592502"
---
# <a name="search-the-schema-set"></a>Durchsuchen des Schemasets

Der **XML-Schema-Explorer** ermöglicht das Durchsuchen des Schemas auf folgende Weise:

- Schlüsselwortsuche

- Schemaspezifische Suche

## <a name="keyword-search"></a>Schlüsselwortsuche

Sie führen eine Schlüsselwort Suche durch, indem Sie eine Teil Zeichenfolge in das Textfeld **Suchen Schemaset** der Symbolleiste des **XML-Schema-Explorers** eingeben

![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

Der **XML-Schema-Explorer** durchsucht den Schemaset nach den folgenden Attributen:

- Alle `name`- oder `ref`-Attribute, die mit dem angegebenen Schlüsselwort übereinstimmen. Sie können Elemente, Attribute, Typen usw. nach Namen suchen.

- Die `schemaLocation`-Attribute von Include-Anweisungen.

- Die `namespace`-Attribute von Import-Anweisungen.

## <a name="schema-specific-search"></a>Schema spezifische Suche

Der **XML-Schema-Explorer** enthält auch integrierte Suchvorgänge, auf die Sie über das Kontextmenü (Rechtsklick) des XML- **Schema-Explorers**zugreifen können. Weitere Informationen zu verfügbaren Kontextmenüs finden Sie unter [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md). Sie können auch eine Schema spezifische Suche in der Start Ansicht ausführen. Weitere Informationen finden Sie im Abschnitt "Details zum Schemaset" im Thema " [Start Ansicht](../xml-tools/start-view.md) ".

## <a name="display-and-navigate-search-results"></a>Anzeigen und Navigieren in den Suchergebnissen

Nach der Suche wird der Symbolleiste ein Bereich mit der Ergebniszusammenfassung der Suche hinzugefügt. Die Suchergebnisse werden auch im XML- **Schema-Explorer** hervorgehoben und auf der vertikalen Schiebe Leiste durch Ticks gekennzeichnet. Sie können in den Suchergebnissen navigieren, indem Sie auf der Symbolleiste des **XML-Schema-Explorers** im Ergebnisbereich "Zusammenfassung" auf die Schaltflächen " **Gehe zur nächsten Suchergebnis** " klicken. mithilfe der Tastaturtasten **F3** und **UMSCHALT**+**F3**; oder klicken Sie auf die Teil Striche in der Bild Lauf Leiste.

Sie können die Suchergebnisse dem Arbeitsbereich hinzufügen, indem Sie im Zusammenfassungs Ergebnisbereich auf die Schaltfläche **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.

![Suchergebnis des XML-Schema-Explorers](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Suchergebnisse löschen

Um die Suchergebnisse zu löschen, klicken Sie auf der Symbolleiste des **XML-Schema-Explorers** im Zusammenfassungs Ergebnisbereich auf die Schaltfläche **x** .

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)

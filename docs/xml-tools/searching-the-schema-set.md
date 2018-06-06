---
title: XML-Schema-Explorer - Schemaset suchen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1133d6a67442bde5a9f949553efcffd07e2d3ffe
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751740"
---
# <a name="search-the-schema-set"></a>Das Schemaset suchen

Die **XML-Schema-Explorer** können Sie das Schemaset auf folgende Weise zu suchen:

-   Schlüsselwortsuche

-   Schemaspezifische Suche

## <a name="keyword-search"></a>Schlüsselwortsuche

 Sie Schlüsselwort-Suchvorgänge ausführen, indem eine Teilzeichenfolge in der **Schlüsselwortsuche** Textfeld mit der die **XML-Schema-Explorer** Symbolleiste.

 ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

 Die **XML-Schema-Explorer** durchsucht das Schemaset für die folgenden Attribute:

-   Alle `name`- oder `ref`-Attribute, die mit dem angegebenen Schlüsselwort übereinstimmen. Sie können Elemente, Attribute, Typen usw., anhand des Namens suchen.

-   Die `schemaLocation`-Attribute von Include-Anweisungen.

-   Die `namespace`-Attribute von Import-Anweisungen.

## <a name="schema-specific-search"></a>Schemaspezifische Suche

 Die **XML-Schema-Explorer** enthält auch integrierte Suchfunktionen, die Sie zugreifen können, das Kontextmenü des mit der **XML-Schema-Explorer**. Weitere Informationen zu verfügbaren Kontextmenüs zu sehen, finden Sie unter [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md). In dieser Ansicht können Sie außerdem eine schemaspezifische Suche ausführen; Weitere Informationen finden Sie im Abschnitt "Details zum Schemaset" in der [Ausgangsansicht](../xml-tools/start-view.md) Thema.

## <a name="display-and-navigate-search-results"></a>Anzeigen und Suchergebnissen navigieren

 Nach der Suche wird der Symbolleiste ein Bereich mit der Ergebniszusammenfassung der Suche hinzugefügt. Die Suchergebnisse werden auch hervorgehoben, der **XML-Schema-Explorer** und auf der vertikalen Bildlaufleiste durch Teilstriche markiert. Sie können die Suchergebnissen navigieren, indem die **wechseln zum nächsten Suchergebnis** und **wechseln zum vorherigen Suchergebnis** Schaltflächen im Bereich Zusammenfassung der Ergebnisse von der **XML-Schema-Explorer**Symbolleiste; Drücken Sie die Tasten mit **F3** und **UMSCHALT**+**F3**; oder durch Klicken auf die Teilstriche auf der Bildlaufleiste.

 Sie können die Suchergebnisse dem Arbeitsbereich hinzufügen, durch Klicken auf die **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** Schaltfläche im Bereich Zusammenfassung der Ergebnisse.

 ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Löschen der Suchergebnisse

 Um die Suchergebnisse zu löschen, klicken Sie auf die **x** Schaltfläche im Bereich Zusammenfassung der Ergebnisse der **XML-Schema-Explorer** suchsymbolleiste.

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)
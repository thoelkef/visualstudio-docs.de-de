---
title: 'XML-Schema-Explorer: Durchsuchen des Schemasets'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfbc41b24dd0e58dd24e0af99afe458d27f8ade6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930856"
---
# <a name="search-the-schema-set"></a>Durchsuchen des Schemasets

Die **XML-Schema-Explorer** ermöglicht es Ihnen, suchen Sie das Schema auf folgende Weise festlegen:

-   Schlüsselwortsuche

-   Schemaspezifische Suche

## <a name="keyword-search"></a>Schlüsselwortsuche

 Durchführen von Schlüsselwortsuchen durch Eingabe einer Teilzeichenfolge in der **Schlüsselwortsuche** Textfeld die **XML-Schema-Explorer** Symbolleiste.

 ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

 Die **XML-Schema-Explorer** durchsucht das Schemaset für die folgenden Attribute:

-   Alle `name`- oder `ref`-Attribute, die mit dem angegebenen Schlüsselwort übereinstimmen. Sie finden die Elemente, Attribute, Typen und So weiter, anhand des Namens.

-   Die `schemaLocation`-Attribute von Include-Anweisungen.

-   Die `namespace`-Attribute von Import-Anweisungen.

## <a name="schema-specific-search"></a>Schemaspezifische Suche

 Die **XML-Schema-Explorer** enthält auch integrierte Suchfunktionen, die Sie zugreifen können, mithilfe des Kontextmenüs (Rechtsklick), der die **XML-Schema-Explorer**. Weitere Informationen zu verfügbaren Kontextmenüs finden Sie unter [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md). Sie können auch eine schemaspezifische Suche aus der Ausgangsansicht ausführen; Weitere Informationen finden Sie im Abschnitt "Details zum Schemaset" in der [Ausgangsansicht](../xml-tools/start-view.md) Thema.

## <a name="display-and-navigate-search-results"></a>Anzeigen und Suchergebnissen navigieren

 Nach der Suche wird der Symbolleiste ein Bereich mit der Ergebniszusammenfassung der Suche hinzugefügt. Die Ergebnisse der Suche werden auch hervorgehoben, der **XML-Schema-Explorer** und auf der vertikalen Bildlaufleiste durch Teilstriche markiert. Sie können die Suchergebnissen navigieren, indem die **wechseln Sie zum nächsten Suchergebnis** und **wechseln Sie zum vorherigen Suchergebnis** Schaltflächen im Bereich Zusammenfassung der Ergebnisse der der **XML-Schema-Explorer**Symbolleiste Mithilfe der Tastatur **F3** und **UMSCHALT**+**F3**; oder durch Klicken auf die Teilstriche in der Bildlaufleiste.

 Sie können die Ergebnisse der Suche mit dem Arbeitsbereich hinzufügen, indem Sie auf die **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** auf den Bereich auf die Schaltfläche.

 ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Löschen der Suchergebnisse

 Um die Suchergebnisse zu löschen, klicken Sie auf die **x** im Bereich Zusammenfassung der Ergebnisse der Schaltfläche die **XML-Schema-Explorer** Suche Toolbar.

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)
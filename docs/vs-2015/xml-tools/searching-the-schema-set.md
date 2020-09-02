---
title: Durchsuchen des Schema Satzes | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e3a8563d5e2cd29c9c521761498d7ef87b7cbab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656155"
---
# <a name="searching-the-schema-set"></a>Durchsuchen des Schemasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im XML-Schema-Explorer stehen Ihnen die folgenden Methoden zum Durchsuchen des Schemasets zur Verfügung:

- Schlüsselwortsuche

- Schemaspezifische Suche

## <a name="keyword-search"></a>Schlüsselwortsuche
 Geben Sie zum Ausführen einer Schlüsselwortsuche eine Teilzeichenfolge in das Textfeld **Schemaset suchen** auf der XML-Schema-Explorer-Symbolleiste ein.

 ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 Der XML-Schema-Explorer durchsucht das Schemaset nach Folgendem:

- Alle `name`- oder `ref`-Attribute, die mit dem angegebenen Schlüsselwort übereinstimmen. So können Sie anhand des Namens nach Elementen, Attributen, Typen usw. suchen.

- Die `schemaLocation`-Attribute von Include-Anweisungen.

- Die `namespace`-Attribute von Import-Anweisungen.

## <a name="schema-specific-search"></a>Schemaspezifische Suche
 Der XML-Schema-Explorer enthält auch integrierte Suchfunktionen, auf die Sie über das Kontextmenü des XML-Schema-Explorers zugreifen. Weitere Informationen zu verfügbaren Kontextmenüs finden Sie unter [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md). Sie können auch eine schemaspezifische Suche in der Ausgangsansicht ausführen. Weitere Informationen dazu finden Sie im Abschnitt „Details zum Schemaset“ im Thema [Ausgangsansicht](../xml-tools/start-view.md).

## <a name="displaying-and-navigating-search-results"></a>Anzeigen von Suchergebnissen und Navigieren in den Ergebnissen
 Nach der Suche wird der Symbolleiste ein Bereich mit der Ergebniszusammenfassung der Suche hinzugefügt. Die Suchergebnisse werden auch im XML-Schema-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert. Sie können in den Suchergebnissen navigieren, indem Sie auf der Symbolleiste des **XML-Schema** -Explorers im Ergebnisbereich "Zusammenfassung" auf die Schaltflächen " **Gehe zur nächsten Suchergebnis** " klicken. mithilfe der Tastaturtasten F3 und UMSCHALT + F3; oder klicken Sie auf die Teil Striche in der Bild Lauf Leiste.

 Sie können die Suchergebnisse dem Arbeitsbereich hinzufügen, indem Sie im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **Hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.

 ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>Löschen der Suchergebnisse
 Klicken Sie auf der XML-Schema-Explorer-Suchsymbolleiste im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **x**, um die Suchergebnisse zu löschen.

## <a name="see-also"></a>Weitere Informationen
 [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)

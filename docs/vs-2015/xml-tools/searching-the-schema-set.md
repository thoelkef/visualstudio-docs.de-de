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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656155"
---
# <a name="searching-the-schema-set"></a>Durchsuchen des Schemasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im XML-Schema-Explorer stehen Ihnen die folgenden Methoden zum Durchsuchen des Schemasets zur Verfügung:

- Schlüsselwortsuche

- Schemaspezifische Suche

## <a name="keyword-search"></a>Schlüsselwortsuche
 Sie führen eine Schlüsselwort Suche durch, indem Sie eine Teil Zeichenfolge in das Textfeld **Suchen Schemaset** der Symbolleiste des XML-Schema-Explorers eingeben

 ![XML Schema Explorer-Schlüsselwort Suche](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 Der XML-Schema-Explorer durchsucht das Schemaset nach Folgendem:

- Alle `name`- oder `ref`-Attribute, die mit dem angegebenen Schlüsselwort übereinstimmen. So können Sie anhand des Namens nach Elementen, Attributen, Typen usw. suchen.

- Die `schemaLocation`-Attribute von Include-Anweisungen.

- Die `namespace`-Attribute von Import-Anweisungen.

## <a name="schema-specific-search"></a>Schemaspezifische Suche
 Der XML-Schema-Explorer enthält auch integrierte Suchfunktionen, auf die Sie über das Kontextmenü des XML-Schema-Explorers zugreifen. Weitere Informationen zu verfügbaren Kontextmenüs finden Sie unter [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md). Sie können auch eine Schema spezifische Suche in der Start Ansicht ausführen. Weitere Informationen finden Sie im Abschnitt "Details zum Schemaset" im Thema " [Start Ansicht](../xml-tools/start-view.md) ".

## <a name="displaying-and-navigating-search-results"></a>Anzeigen von Suchergebnissen und Navigieren in den Ergebnissen
 Nach der Suche wird der Symbolleiste ein Bereich mit der Ergebniszusammenfassung der Suche hinzugefügt. Die Suchergebnisse werden auch im XML-Schema-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert. Sie können in den Suchergebnissen navigieren, indem Sie auf der Symbolleiste des **XML-Schema** -Explorers im Ergebnisbereich "Zusammenfassung" auf die Schaltflächen " **Gehe zur nächsten Suchergebnis** " klicken. mithilfe der Tastaturtasten F3 und UMSCHALT + F3; oder klicken Sie auf die Teil Striche in der Bild Lauf Leiste.

 Sie können die Suchergebnisse dem Arbeitsbereich hinzufügen, indem Sie im Zusammenfassungs Ergebnisbereich auf die Schaltfläche **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.

 ![Suchergebnis des XML-Schema-Explorers](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>Löschen der Suchergebnisse
 Um die Suchergebnisse zu löschen, klicken Sie auf der Symbolleiste des XML-Schema-Explorers im Zusammenfassungs Ergebnisbereich auf die Schaltfläche **x** .

## <a name="see-also"></a>Siehe auch
 [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)

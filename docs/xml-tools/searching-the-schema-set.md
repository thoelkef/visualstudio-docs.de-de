---
title: Durchsuchen des Schemasets | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6bef5c0358ecdadb5f8f9aada4e69d748b3fa14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="searching-the-schema-set"></a>Durchsuchen des Schemasets
Im XML-Schema-Explorer stehen Ihnen die folgenden Methoden zum Durchsuchen des Schemasets zur Verfügung:  
  
-   Schlüsselwortsuche  
  
-   Schemaspezifische Suche  
  
## <a name="keyword-search"></a>Schlüsselwortsuche  
 Sie Schlüsselwort-Suchvorgänge ausführen, indem eine Teilzeichenfolge in der **Schlüsselwortsuche** Textfeld der XML-Schema-Explorer-Symbolleiste.  
  
 ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 Der XML-Schema-Explorer durchsucht das Schemaset nach Folgendem:  
  
-   Alle `name`- oder `ref`-Attribute, die mit dem angegebenen Schlüsselwort übereinstimmen. So können Sie anhand des Namens nach Elementen, Attributen, Typen usw. suchen.  
  
-   Die `schemaLocation`-Attribute von Include-Anweisungen.  
  
-   Die `namespace`-Attribute von Import-Anweisungen.  
  
## <a name="schema-specific-search"></a>Schemaspezifische Suche  
 Der XML-Schema-Explorer enthält auch integrierte Suchfunktionen, auf die Sie über das Kontextmenü des XML-Schema-Explorers zugreifen. Weitere Informationen zu verfügbaren Kontextmenüs zu sehen, finden Sie unter [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md). In dieser Ansicht können Sie außerdem eine schemaspezifische Suche ausführen; Weitere Informationen finden Sie im Abschnitt "Details zum Schemaset" in der [Ausgangsansicht](../xml-tools/start-view.md) Thema.  
  
## <a name="displaying-and-navigating-search-results"></a>Anzeigen von Suchergebnissen und Navigieren in den Ergebnissen  
 Nach der Suche wird der Symbolleiste ein Bereich mit der Ergebniszusammenfassung der Suche hinzugefügt. Die Suchergebnisse werden auch im XML-Schema-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert. Sie können die Suchergebnissen navigieren, indem die **wechseln zum nächsten Suchergebnis** und **wechseln zum vorherigen Suchergebnis** Schaltflächen im Bereich Zusammenfassung der Ergebnisse von der XML-Schema-Explorer-Symbolleiste; mithilfe der Tastatur F3 und UMSCHALT + F3; oder durch Klicken auf die Teilstriche auf der Bildlaufleiste.  
  
 Sie können die Suchergebnisse dem Arbeitsbereich hinzufügen, durch Klicken auf die **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** Schaltfläche im Bereich Zusammenfassung der Ergebnisse.  
  
 ![Suchergebnis des XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>Löschen der Suchergebnisse  
 Um die Suchergebnisse zu löschen, klicken Sie auf die **x** Schaltfläche der XML-Schema-Explorer-suchsymbolleiste im Bereich Zusammenfassung der Ergebnisse.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)
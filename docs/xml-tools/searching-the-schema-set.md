---
title: "Durchsuchen des Schemasets | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Durchsuchen des Schemasets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im XML\-Schema\-Explorer stehen Ihnen die folgenden Methoden zum Durchsuchen des Schemasets zur Verfügung:  
  
-   Schlüsselwortsuche  
  
-   Schemaspezifische Suche  
  
## Schlüsselwortsuche  
 Geben Sie zum Ausführen einer Schlüsselwortsuche eine Teilzeichenfolge in das Textfeld **Schemaset suchen** auf der XML\-Schema\-Explorer\-Symbolleiste ein.  
  
 ![Schlüsselwortsuche im XML&#45;Schema&#45;Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 Der XML\-Schema\-Explorer durchsucht das Schemaset nach Folgendem:  
  
-   Alle `name`\- oder `ref`\-Attribute, die mit dem angegebenen Schlüsselwort übereinstimmen.So können Sie anhand des Namens nach Elementen, Attributen, Typen usw. suchen.  
  
-   Die `schemaLocation`\-Attribute von Include\-Anweisungen.  
  
-   Die `namespace`\-Attribute von Import\-Anweisungen.  
  
## Schemaspezifische Suche  
 Der XML\-Schema\-Explorer enthält auch integrierte Suchfunktionen, auf die Sie über das Kontextmenü des XML\-Schema\-Explorers zugreifen.Weitere Informationen zu verfügbaren Kontextmenüs finden Sie unter [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md).Sie können auch eine schemaspezifische Suche in der Ausgangsansicht ausführen. Weitere Informationen dazu finden Sie im Abschnitt "Details zum Schemaset" im Thema [Ausgangsansicht](../xml-tools/start-view.md).  
  
## Anzeigen von Suchergebnissen und Navigieren in den Ergebnissen  
 Nach der Suche wird der Symbolleiste ein Bereich mit der Ergebniszusammenfassung der Suche hinzugefügt.Die Suchergebnisse werden auch im XML\-Schema\-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.Sie können wie folgt in den Suchergebnissen navigieren: Klicken Sie auf der XML\-Schema\-Explorer\-Symbolleiste auf die Schaltflächen **Zum nächsten Suchergebnis** und **Zum vorherigen Suchergebnis**, drücken Sie die Tasten F3 und UMSCHALT\+F3, oder klicken Sie auf die Teilstriche in der Bildlaufleiste.  
  
 Sie können die Suchergebnisse dem Arbeitsbereich hinzufügen, indem Sie im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **Hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.  
  
 ![Suchergebnis im XML&#45;Schema&#45;Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## Löschen der Suchergebnisse  
 Klicken Sie auf der XML\-Schema\-Explorer\-Suchsymbolleiste im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **x**, um die Suchergebnisse zu löschen.  
  
## Siehe auch  
 [XML\-Schema\-Explorer](../xml-tools/xml-schema-explorer.md)
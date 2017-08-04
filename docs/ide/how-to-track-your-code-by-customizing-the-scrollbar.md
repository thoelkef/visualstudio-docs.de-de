---
title: "Gewusst wie: Nachverfolgen von Code durch Anpassen der Schiebeleiste | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Gewusst wie: Nachverfolgen von Code durch Anpassen der Schiebeleiste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Ihre Dateien lange Codefolgen enthalten, kann dies Ihre Arbeit erschweren.  Sie können die Bildlaufleiste des Codefensters anpassen, um den Code aus der Vogelperspektive zu betrachten.  
  
### So zeigen Sie Anmerkungen auf der Bildlaufleiste an  
  
1.  Sie können die Bildlaufleiste so einrichten, dass Codeänderungen, Haltepunkte, Fehler und Lesezeichen angezeigt werden.  
  
     Öffnen Sie die Seite mit Optionen der **Bildlaufleiste** \(**Tools, Optionen, Text\-Editor, Alle Sprachen** oder eine bestimmte Sprache, oder geben Sie "Bildlaufleiste" im Fenster **Schnellstart** an\).  
  
2.  Wählen Sie **Anmerkungen über vertikaler Bildlaufleiste anzeigen** aus, und klicken Sie auf die Anmerkungen, die angezeigt werden sollen.  \(Die Option **Markierungen** umfasst Haltepunkte und Lesezeichen.\)  
  
3.  Probieren Sie es aus.  Öffnen Sie eine große Codedatei, und ersetzen Sie ein Element, das an mehreren Stellen in der Datei vorkommt.  Die Bildlaufleiste zeigt die Auswirkungen der Ersetzungen an. Sie können also Änderungen rückgängig machen, wenn ein Element nicht ersetzt werden soll.  
  
     So sieht die Bildlaufleiste aus, nachdem eine Zeichenfolge gesucht wurde.  Sie Sie sehen, werden alle Instanzen der Zeichenfolge angezeigt.  
  
     ![Bildlaufleiste nach der Suche nach einer Zeichenfolge](~/ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")  
  
     So sieht die Bildlaufleiste aus, nachdem alle Instanzen der Zeichenfolge ersetzt wurden.  Sie können sofort sehen, dass der Vorgang Probleme verursacht hat.  
  
     ![Bildlaufleiste nach dem Ersetzen einer Zeichenfolge mit Fehlern](~/ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")  
  
### So legen Sie den Anzeigemodus für die Bildlaufleiste fest  
  
1.  Die Bildlaufleiste verfügt über den Leistenmodus \(Standardeinstellung\) und den Zuordnungsmodus.  Im Leistenmodus werden nur Anmerkungsindikatoren auf der Bildlaufleiste angezeigt.  Im Zuordnungsmodus werden die Codezeilen auf der Bildlaufleiste dargestellt.  Sie können deren Breite auswählen und angeben, ob der zugrunde liegende Code angezeigt werden soll, wenn Sie mit dem Cursor darauf zeigen.  Wenn Sie auf eine Stelle der Bildlaufleiste klicken, springt der Cursor zu der entsprechenden Position im Code.  Ausgeblendete Bereiche sind anders schattiert und werden eingeblendet, wenn Sie darauf doppelklicken.  
  
     Wählen Sie auf der Seite mit Optionen der **Bildlaufleiste** entweder **Leistenmodus für vertikale Bildlaufleiste verwenden** oder **Zuordnungsmodus für vertikale Bildlaufleiste verwenden** aus.  Sie können die Breite in der Dropdownliste **Quellenübersicht** auswählen.  
  
     Im Folgenden wird gezeigt, wie das Suchbeispiel aussieht, wenn der Zuordnungsmodus aktiviert ist und die Breite auf "Mittel" festgelegt ist:  
  
     ![Bildlaufleiste im Zuordnungsmodus](~/ide/media/enhancedscrollbar.png "EnhancedScrollbar")  
  
2.  Wählen Sie im Zuordnungsmodus die Option **Vorschau\-QuickInfo anzeigen** aus, um eine Vorschau des Codes zu aktivieren, wenn Sie den Cursor auf der Bildlaufleiste nach oben und unten bewegen.  Hier das Ergebnis:  
  
     ![Bildlaufleiste mit einer QuickInfo](~/ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")  
  
     Wenn Sie das Verhalten der Bildlaufleiste im Zuordnungsmodus beibehalten und die Vorschau\-QuickInfo anzeigen möchten, nicht aber die Quellcodeübersicht, dann legen Sie die Option für **Quellenübersicht** auf **Aus** fest.
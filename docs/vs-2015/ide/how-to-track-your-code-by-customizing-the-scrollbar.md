---
title: 'Vorgehensweise: Verfolgen von Code durch Anpassen der Scrollleiste | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 11df0e3ca4e8b9c814bf91735d48bb091c711068
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788205"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Gewusst wie: Verfolgen von Code durch Anpassen der Scrollleiste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Ihre Dateien lange Codefolgen enthalten, kann dies Ihre Arbeit erschweren. Sie können die Bildlaufleiste des Codefensters anpassen, um den Code aus der Vogelperspektive zu betrachten.  
  
### <a name="to-show-annotations-on-the-scroll-bar"></a>So zeigen Sie Anmerkungen auf der Bildlaufleiste an  
  
1.  Sie können die Bildlaufleiste so einrichten, dass Codeänderungen, Haltepunkte, Fehler und Lesezeichen angezeigt werden.  
  
     Öffnen Sie die Seite mit Optionen der **Bildlaufleiste** (**Extras > Optionen > Text-Editor > Alle Sprachen** oder eine bestimmte Sprache, oder geben Sie **Bildlaufleiste** im Fenster Schnellstart an).  
  
2.  Wählen Sie **Anmerkungen über vertikaler Bildlaufleiste anzeigen** aus, und klicken Sie auf die Anmerkungen, die angezeigt werden sollen. (Die Option **Markierungen** umfasst Haltepunkte und Lesezeichen.)  
  
3.  Probieren Sie es aus. Öffnen Sie eine große Codedatei, und ersetzen Sie ein Element, das an mehreren Stellen in der Datei vorkommt. Die Bildlaufleiste zeigt die Auswirkungen der Ersetzungen an. Sie können also Änderungen rückgängig machen, wenn ein Element nicht ersetzt werden soll.  
  
     So sieht die Bildlaufleiste aus, nachdem eine Zeichenfolge gesucht wurde. Sie Sie sehen, werden alle Instanzen der Zeichenfolge angezeigt.  
  
     ![Bildlaufleiste nach der Suche nach einer Zeichenfolge.](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")  
  
     So sieht die Bildlaufleiste aus, nachdem alle Instanzen der Zeichenfolge ersetzt wurden. Sie können sofort sehen, dass der Vorgang Probleme verursacht hat.  
  
     ![Bildlaufleiste nach dem Ersetzen einer Zeichenfolge mit Fehlern](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")  
  
### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>So legen Sie den Anzeigemodus für die Bildlaufleiste fest  
  
1.  Die Bildlaufleiste verfügt über den Leistenmodus (Standardeinstellung) und den Zuordnungsmodus. Im Leistenmodus werden nur Anmerkungsindikatoren auf der Bildlaufleiste angezeigt. Im Zuordnungsmodus werden die Codezeilen auf der Bildlaufleiste dargestellt. Sie können deren Breite auswählen und angeben, ob der zugrunde liegende Code angezeigt werden soll, wenn Sie mit dem Cursor darauf zeigen. Wenn Sie auf eine Stelle der Bildlaufleiste klicken, springt der Cursor zu der entsprechenden Position im Code. Reduzierte Bereiche sind anders schattiert und werden eingeblendet, wenn Sie darauf doppelklicken.  
  
     Wählen Sie auf der Seite mit Optionen der **Bildlaufleiste** entweder **Leistenmodus für vertikale Bildlaufleiste verwenden** oder **Zuordnungsmodus für vertikale Bildlaufleiste** verwenden aus. Sie können die Breite in der Dropdownliste **Quellenübersicht** auswählen.  
  
     Im Folgenden wird gezeigt, wie das Suchbeispiel aussieht, wenn der Zuordnungsmodus aktiviert ist und die Breite auf "Mittel" festgelegt ist:  
  
     ![Bildlaufleiste im Zuordnungsmodus](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")  
  
2.  Wählen Sie im Zuordnungsmodus die Option **Vorschau-QuickInfo anzeigen** aus, um eine Vorschau des Codes zu aktivieren, wenn Sie den Cursor auf der Bildlaufleiste nach oben und unten bewegen. Hier das Ergebnis:  
  
     ![Bildlaufleiste mit einer QuickInfo](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")  
  
     Wenn Sie das Verhalten der Bildlaufleiste im Zuordnungsmodus beibehalten und die Vorschau-QuickInfo anzeigen möchten, nicht aber die Quellcodeübersicht, dann legen Sie die Option für **Quellenübersicht** auf **Aus** fest.

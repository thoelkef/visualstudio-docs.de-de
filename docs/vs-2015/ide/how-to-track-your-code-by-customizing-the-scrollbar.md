---
title: 'Vorgehensweise: Verfolgen von Code durch Anpassen der Scrollleiste | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a852b0e5ac6c6a677caab97279a0b0cb0299d27f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670634"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Gewusst wie: Verfolgen von Code durch Anpassen der Scrollleiste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Ihre Dateien lange Codefolgen enthalten, kann dies Ihre Arbeit erschweren. Sie können die Bildlaufleiste des Codefensters anpassen, um den Code aus der Vogelperspektive zu betrachten.

### <a name="to-show-annotations-on-the-scroll-bar"></a>So zeigen Sie Anmerkungen auf der Bildlaufleiste an

1. Sie können die Bildlaufleiste so einrichten, dass Codeänderungen, Haltepunkte, Fehler und Lesezeichen angezeigt werden.

     Öffnen Sie die Seite Optionen der Bild Lauf **Leiste** (Extras **, Text-Editor für Optionen). Alle Sprachen** oder eine bestimmte Sprache, oder geben Sie die  **Scrollleiste** im Fenster Schnellstart ein).

2. Wählen Sie **Anmerkungen über vertikaler Bildlaufleiste anzeigen** aus, und klicken Sie auf die Anmerkungen, die angezeigt werden sollen. (Die Option **Markierungen** umfasst Haltepunkte und Lesezeichen.)

3. Probieren Sie es jetzt aus. Öffnen Sie eine große Codedatei, und ersetzen Sie etwas, das an mehreren Stellen in der Datei vorkommt. Die Bildlaufleiste zeigt die Auswirkungen der Ersetzungen an. Sie können also Änderungen rückgängig machen, wenn ein Element nicht ersetzt werden soll.

     So sieht die Bildlaufleiste aus, nachdem eine Zeichenfolge gesucht wurde. Sie Sie sehen, werden alle Instanzen der Zeichenfolge angezeigt.

     ![Bildlaufleiste nach der Suche nach einer Zeichenfolge](../ide/media/enhancedscrollbarsearch.png "Enhancedscrollbarsearch")

     So sieht die Bildlaufleiste aus, nachdem alle Instanzen der Zeichenfolge ersetzt wurden. Sie können sofort sehen, dass der Vorgang Probleme verursacht hat.

     ![Bildlaufleiste nach dem Ersetzen einer Zeichenfolge mit Fehlern](../ide/media/enhancedscrollbarreplace.png "Enhancedscrollbarreplace")

### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>So legen Sie den Anzeigemodus für die Bildlaufleiste fest

1. Die Bildlaufleiste verfügt über den Leistenmodus (Standardeinstellung) und den Zuordnungsmodus. Im Leistenmodus werden nur Anmerkungsindikatoren auf der Bildlaufleiste angezeigt. Im Zuordnungsmodus werden die Codezeilen auf der Bildlaufleiste dargestellt. Sie können deren Breite auswählen und angeben, ob der zugrunde liegende Code angezeigt werden soll, wenn Sie mit dem Cursor darauf zeigen. Wenn Sie auf eine Stelle der Bildlaufleiste klicken, springt der Cursor zu der entsprechenden Position im Code. Ausgeblendete Bereiche sind anders schattiert und werden eingeblendet, wenn Sie darauf doppelklicken.

     Wählen Sie auf der Seite mit Optionen der **Bildlaufleiste** entweder **Leistenmodus für vertikale Bildlaufleiste verwenden** oder **Zuordnungsmodus für vertikale Bildlaufleiste** verwenden aus. Sie können die Breite in der Dropdownliste **Quellenübersicht** auswählen.

     Im Folgenden wird gezeigt, wie das Suchbeispiel aussieht, wenn der Zuordnungsmodus aktiviert ist und die Breite auf "Mittel" festgelegt ist:

     ![Bildlaufleiste im Zuordnungsmodus](../ide/media/enhancedscrollbar.png "Enhancedscrollbar")

2. Wählen Sie im Zuordnungsmodus die Option **Vorschau-QuickInfo anzeigen** aus, um eine Vorschau des Codes zu aktivieren, wenn Sie den Cursor auf der Bildlaufleiste nach oben und unten bewegen. So sieht es aus:

     ![Bildlaufleiste mit einer QuickInfo](../ide/media/enhancedscrollbarsearchtooltip.png "Enhancedscrollbarsearchtooltip")

     Wenn Sie das Verhalten der Bildlaufleiste im Zuordnungsmodus beibehalten und die Vorschau-QuickInfo anzeigen möchten, nicht aber die Quellcodeübersicht, dann legen Sie die Option für **Quellenübersicht** auf **Aus** fest.

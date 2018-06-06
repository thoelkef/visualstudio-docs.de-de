---
title: 'Vorgehensweise: Verfolgen von Code durch Anpassen der Scrollleiste'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc18b436a7f25baad9870e36c3224f23de920241
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745736"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Vorgehensweise: Verfolgen von Code durch Anpassen der Scrollleiste

Wenn Ihre Dateien lange Codefolgen enthalten, kann dies Ihre Arbeit erschweren. Sie können die Bildlaufleiste des Codefensters anpassen, um den Code aus der Vogelperspektive zu betrachten.

## <a name="to-show-annotations-on-the-scroll-bar"></a>So zeigen Sie Anmerkungen auf der Bildlaufleiste an

1. Sie können die Bildlaufleiste so einrichten, dass Codeänderungen, Haltepunkte, Fehler und Lesezeichen angezeigt werden.

    Öffnen Sie die Optionsseite **Scrollleiste** über **Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen** oder eine bestimmte Sprache, oder geben Sie **Scrollleiste** im Fenster **Schnellstart** ein.

2. Wählen Sie **Anmerkungen über vertikaler Bildlaufleiste anzeigen** aus, und klicken Sie auf die Anmerkungen, die angezeigt werden sollen.

    Die Option **Markierungen** umfasst Breakpoints und Lesezeichen.

3. Probieren Sie es aus. Öffnen Sie eine große Codedatei, und ersetzen Sie ein Element, das an mehreren Stellen in der Datei vorkommt. Die Bildlaufleiste zeigt die Auswirkungen der Ersetzungen an. Sie können also Änderungen rückgängig machen, wenn ein Element nicht ersetzt werden soll.

    So sieht die Bildlaufleiste aus, nachdem eine Zeichenfolge gesucht wurde. Sie Sie sehen, werden alle Instanzen der Zeichenfolge angezeigt.

    ![Bildlaufleiste nach der Suche nach einer Zeichenfolge](../ide/media/enhancedscrollbarsearch.png)

    So sieht die Bildlaufleiste aus, nachdem alle Instanzen der Zeichenfolge ersetzt wurden. Sie können sofort sehen, dass der Vorgang Probleme verursacht hat.

    ![Bildlaufleiste nach dem Ersetzen einer Zeichenfolge mit Fehlern](../ide/media/enhancedscrollbarreplace.png)

## <a name="to-set-the-display-mode-for-the-scroll-bar"></a>So legen Sie den Anzeigemodus für die Bildlaufleiste fest

1. Die Bildlaufleiste verfügt über zwei Modi: den Leistenmodus (Standardeinstellung) und den Zuordnungsmodus. Im Leistenmodus werden nur Anmerkungsindikatoren auf der Bildlaufleiste angezeigt. Im Zuordnungsmodus werden die Codezeilen auf der Bildlaufleiste dargestellt. Sie können deren Breite auswählen und angeben, ob der zugrunde liegende Code angezeigt werden soll, wenn Sie mit dem Cursor darauf zeigen. Wenn Sie auf eine Stelle der Bildlaufleiste klicken, springt der Cursor zu der entsprechenden Position im Code. Reduzierte Bereiche sind anders schattiert und werden eingeblendet, wenn Sie darauf doppelklicken.

    Wählen Sie auf der Seite mit Optionen der **Bildlaufleiste** entweder **Leistenmodus für vertikale Bildlaufleiste verwenden** oder **Zuordnungsmodus für vertikale Bildlaufleiste** verwenden aus. Sie können die Breite in der Dropdownliste **Quellenübersicht** auswählen.

    Im Folgenden wird gezeigt, wie das Suchbeispiel aussieht, wenn der Zuordnungsmodus aktiviert und die Breite auf **Mittel** festgelegt ist:

    ![Bildlaufleiste im Zuordnungsmodus](../ide/media/enhancedscrollbar.png)

2. Wählen Sie im Zuordnungsmodus die Option **Vorschau-QuickInfo anzeigen** aus, um eine Vorschau des Codes zu aktivieren, wenn Sie den Cursor auf der Bildlaufleiste nach oben und unten bewegen. Hier das Ergebnis:

    ![Bildlaufleiste mit einer QuickInfo](../ide/media/enhancedscrollbarsearchtooltip.png)

    Wenn Sie das Scrollverhalten im Zuordnungsmodus beibehalten und die Vorschau-QuickInfo anzeigen möchten, nicht aber die Quellcodeübersicht, dann legen Sie die Option für **Quellenübersicht** auf **Off** (aus) fest.

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
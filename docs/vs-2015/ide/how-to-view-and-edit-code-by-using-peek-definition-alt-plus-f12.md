---
title: 'Vorgehensweise: Anzeigen und Bearbeiten von Code mithilfe von "Definition einsehen" (Alt + F12) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24db36d6bb3a431d5ee3848eb8a6a794980f919a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777302"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Gewusst wie: Anzeigen und Bearbeiten von Code mithilfe von "Definition einsehen" (Alt+F12)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Befehl **Definition einsehen** können Sie Code anzeigen und bearbeiten, ohne den Code zu verlassen, den Sie gerade schreiben. Mit **Definition einsehen** und **Gehe zu Definition** werden dieselben Informationen angezeigt, wobei mit **Definition einsehen** ein Popupfenster geöffnet wird, und mit **Gehe zu Definition** der Code in einem separaten Codefenster angezeigt wird. **Gehe zu Definition** verursacht einen Wechsel des Kontexts (also des aktiven Codefensters, der aktuellen Zeile und der Cursorposition) zum Codedefinitionsfenster. Mithilfe von **Definition einsehen** können Sie die Definition anzeigen und bearbeiten sowie innerhalb der Definitionsdatei navigieren, ohne Ihre Position in der ursprünglichen Codedatei zu verlassen.  
  
 Sie können **Definition einsehen** mit C#-, Visual Basic- und C++-Code verwenden. In Visual Basic zeigt **Definition einsehen** einen Link zum **Objektkatalog** für Symbole ohne Definitionsmetadaten an (z.B. integrierte .NET Framework-Typen).  
  
> [!IMPORTANT]
>  Sie können diesen Befehl in einer Express-Version von Visual Studio 2013 nicht verwenden.  
  
## <a name="working-with-peek-definition"></a>Arbeiten mit der Peek-Definition  
  
#### <a name="to-open-a-peek-definition-window"></a>So öffnen Sie ein Fenster "Definition einsehen"  
  
1.  Sie finden **Definition einsehen**, indem Sie das Kontextmenü einer Methode öffnen, die Sie durchsuchen möchten. (Tastatur: Alt+F12)  
  
     Diese Abbildung zeigt das Fenster **Definition einsehen** für eine Methode mit dem Namen `Print()`:  
  
     ![Peek-Fenster](../ide/media/peekwindow.png "PeekWindow")  
  
     Das Definitionsfenster wird unter der `printer.Print(“Hello World!”)`-Zeile in der ursprünglichen Datei angezeigt. Das Fenster blendet keinen Code in der ursprünglichen Datei aus. Die Zeilen, die dem Aufruf `printer.Print(“Hello World!”)` folgen, werden im Definitionsfenster angezeigt.  
  
2.  Sie können den Cursor im Codedefinitionsfenster an unterschiedliche Positionen verschieben. Sie können sich im ursprünglichen Codefenster über oder unter dem Definitionsfenster frei bewegen.  
  
3.  Sie können eine Zeichenfolge aus dem Definitionsfenster kopieren und in den ursprünglichen Code einfügen. Sie können die Zeichenfolge auch per Drag & Drop aus dem Definitionsfenster in den ursprünglichen Code verschieben. Sie wird allerdings nicht im Definitionsfenster gelöscht.  
  
4.  Sie können das Definitionsfenster schließen, indem Sie die ESC-TASTE oder auf die Schaltfläche **Schließen** auf der Definitionsfensterregisterkarte klicken.  
  
#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>So öffnen Sie ein Fenster "Definition einsehen" in einem Fenster "Definition einsehen"  
  
-   Wenn bereits ein Fenster **Definition einsehen** geöffnet ist, können Sie **Definition ansehen** für den Code in diesem Fenster erneut aufrufen. Ein weiteres Definitionsfenster wird geöffnet. Ein Satz von Breadcrumbpunkten wird neben der Definitionsfensterregisterkarte, die Sie zum Navigieren zwischen Definitionsfenstern verwenden können, angezeigt. Die QuickInfo für die einzelnen Punkte zeigt jeweils den Namen und den Pfad der von den Punkten dargestellten Definitionsdatei an.  
  
     ![Peek-Fenster innerhalb eines Peek-Fensters](../ide/media/peekwithinpeek.png "PeekWithinPeek")  
  
#### <a name="to-use-peek-definition-with-multiple-results"></a>So verwenden Sie die Peek-Definition mit mehreren Ergebnissen  
  
-   Wenn Sie **Definition einsehen** für Code verwenden, für den mehrere Definitionen vorliegen, (z.B. bei partiellen Klassen), wird rechts neben dem Codedefinitionsfenster eine Ergebnisliste angezeigt. Sie können jedes Ergebnis in der Liste auswählen, um dessen Definition anzuzeigen.  
  
     ![Peek-Fenster aus verschiedenen Ergebnissen](../ide/media/peekmultiple.png "PeekMultiple")  
  
#### <a name="to-edit-inside-the-peek-definition-window"></a>So bearbeiten Sie innerhalb des Fensters "Definition einsehen"  
  
-   Wenn Sie die Bearbeitung innerhalb eines **Definition einsehen**-Fensters beginnen, wird die Datei, die Sie ändern, automatisch als separate Registerkarte im Code-Editor geöffnet. Die Datei spiegelt dann die bereits von Ihnen vorgenommenen Änderungen wider. Sie können weiterhin Änderungen im **Definition einsehen**-Fenster vornehmen, rückgängig machen und speichern, und die Registerkarte spiegelt weiterhin diese Änderungen wider. Auch wenn Sie das Fenster schließen, ohne die Änderungen zu speichern, können Sie weitere Änderungen auf der Registerkarte vornehmen, rückgängig machen und speichern, indem Sie genau da weitermachen, wo Sie im Fenster aufgehört hatten.  
  
     ![Bearbeiten innerhalb eines Peek-Fensters](../ide/media/peekedit.png "PeekEdit")  
  
#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>So verwenden Sie Tastenkombinationen für die Peek-Definition  
  
-   Im Fenster **Definition einsehen** können Sie diese Tastenkombinationen verwenden:  
  
    |Funktionalität|Tastenkombination|  
    |-------------------|-----------------------|  
    |Öffnen des Definitionsfensters|Alt+F12|  
    |Schließen des Definitionsfensters|Esc|  
    |Höherstufen des Definitionsfensters auf eine reguläre Dokumentregisterkarte|UMSCHALT+ALT+POS1|  
    |Wechseln zwischen Definitionsfenstern|STRG+ALT+- und STRG+ALT+=|  
    |Zwischen mehreren Ergebnissen navigieren|F8 und UMSCHALT+F8|  
    |Umschalten zwischen den Fenstern "Code-Editor" und "Definition"|UMSCHALT+ESC|  
  
    > [!NOTE]
    >  Sie können die gleichen Tastenkombinationen zum Bearbeiten in einem **Definition einsehen**-Fenster verwenden, die Sie an anderer Stelle in Visual Studio nutzen.  
  
## <a name="see-also"></a>Siehe auch  
 [Produktivitätstipps](../ide/productivity-tips-for-visual-studio.md)

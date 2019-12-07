---
title: 'Überprüfen von Variablen: Auto-und lokale Fenster | Microsoft-Dokumentation'
ms.custom: seodec18
ms.date: 10/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b159f631534135ac568fb03dbffa46ae0360fc47
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2019
ms.locfileid: "74904090"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Überprüfen von Variablen in den Fenstern Auto und lokal

In **den** Fenstern **Auto und lokal** werden Variablen Werte angezeigt, während Sie Debuggen. Die Fenster sind nur während einer Debugsitzung verfügbar. Im **Fenster Auto** werden Variablen angezeigt, die um den aktuellen Haltepunkt verwendet werden. Das **Fenster Lokal** zeigt Variablen an, die im lokalen Gültigkeitsbereich definiert sind, in der Regel die aktuelle Funktion oder Methode. Wenn Sie den Code zum ersten Mal debuggen möchten, sollten Sie vor dem Durcharbeiten dieses Artikels das [Debuggen für absolute Einsteiger](../debugger/debugging-absolute-beginners.md) und [Debuggingtechniken und-Tools](../debugger/write-better-code-with-visual-studio.md) lesen.

 Das **Fenster** Auto ist für C#, Visual Basic, C++und Python-Code, jedoch nicht für JavaScript oder F#verfügbar.

Wählen Sie zum **Öffnen des Fensters Auto beim** Debuggen die Option **Debuggen** > **Windows** ** > Auto**aus, oder drücken Sie **STRG**+**alt**+**V** > **A**.

Um das Fenster Lokal zu **Öffnen, wählen** **Sie beim** Debuggen die Option **Debuggen** > **Fenster** > lokal, oder drücken Sie **alt**+**4**.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Visual Studio für Mac finden Sie unter [Datenvisualisierungen in Visual Studio für Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Verwenden der Fenster "Auto" und "lokal"

Arrays **und Objekte werden in den Fenstern** "Auto **" und "** lokal" als Struktur Steuerelemente angezeigt. Wählen Sie den Pfeil links neben einem Variablennamen aus, um die Ansicht zu erweitern und Felder und Eigenschaften anzuzeigen. Im folgenden finden Sie ein Beispiel für ein <xref:System.IO.FileStream?displayProperty=fullName> Objekt **im Fenster "** lokal":

![Lokale Dateien (FILESTREAM)](../debugger/media/locals-filestream.png "Locals-FileStream")

Ein roter Wert **im Fenster "** lokal **" oder "** Auto" bedeutet, dass sich der Wert seit der letzten Auswertung geändert hat. Die Änderung kann aus einer vorherigen Debugsitzung bestehen, oder weil Sie den Wert im Fenster geändert haben.

Das standardmäßige numerische Format in Debuggerfenstern ist Decimal. Um es in Hexadezimal zu ändern, klicken Sie mit **der rechten** Maustaste in **das Fenster Lokal** oder Auto, und wählen Sie **Hexadezimale Anzeige**aus. Diese Änderung wirkt sich auf alle Debuggerfenster aus.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Bearbeiten von Variablen Werten im Fenster "Auto" oder "lokal"

Doppelklicken Sie auf den Wert, und geben Sie den neuen Wert ein, um die Werte der meisten Variablen in **den Fenstern "** Auto **" oder "** lokal" zu bearbeiten.

Sie können Sie einen Ausdruck für einen Wert eingeben, etwa `a + b`. Der Debugger akzeptiert im die meisten gültigen Sprachausdrücke.

In nativem C++-Code müssen Sie möglicherweise den Kontext eines Variablennamens qualifizieren. Weitere Informationen finden Sie unter [Kontextoperator (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Stellen Sie sicher, dass Sie die Konsequenzen verstehen, bevor Sie Werte und Ausdrücke ändern. Mögliche Probleme:
>
>- Die Auswertung bestimmter Ausdrücke kann zur Änderung des Werts einer Variablen führen oder sich auf den Programmzustand auswirken. Beispielsweise wird durch Auswerten von `var1 = ++var2` der Wert sowohl `var1` als auch `var2`geändert. Diese Ausdrücke haben [Nebeneffekte](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Nebeneffekte können unerwartete Ergebnisse verursachen, wenn Sie sich nicht bewusst sind.
>
>- Das Bearbeiten von Gleitkommawerten kann aufgrund der Dezimal-zu-Binär-Konvertierung von Nachkommastellen zu geringfügigen Ungenauigkeiten führen. Auch eine scheinbar harmlose Bearbeitung kann zu Änderungen an einigen Bits in der Gleit Komma Variablen führen.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Im Fenster "Auto" oder "lokal" suchen

Sie können nach Schlüsselwörtern in den Spalten Name, Wert und Typ des Fensters Auto **oder lokal** suchen, indem Sie die Suchleiste oberhalb der **einzelnen Fenster verwenden** . Drücken Sie die EINGABETASTE, oder wählen Sie einen der Pfeile aus, um eine Suche auszuführen. Zum Abbrechen einer laufenden Suche wählen Sie das Symbol "x" in der Suchleiste aus.

Verwenden Sie die Pfeile nach links und rechts (UMSCHALT + F3 bzw. F3), um zwischen gefundenen Übereinstimmungen zu navigieren.

![Im Fenster "lokal" suchen](../debugger/media/ee-search-locals.png "Im Fenster "lokal" suchen")

Um die Suche zu **erhöhen oder zu** erhöhen, verwenden Sie die Dropdown Liste **tiefer suchen** am oberen Rand **des Fensters Auto oder lokal** , um auszuwählen, wie viele Ebenen tief in geschaltete Objekte durchsucht werden sollen. 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>PIN-Eigenschaften im Fenster "Auto" oder "lokal"

> [!NOTE]
> Dieses Feature wird für .net Core 3,0 oder höher unterstützt.

Sie können Objekte **mithilfe der Eigenschaften in den Fenstern** "Auto" und "lokal" schnell überprüfen.  Um dieses Tool zu verwenden, zeigen Sie auf eine Eigenschaft, und wählen Sie das angezeigte anheft Symbol aus, und wählen Sie im resultierenden Kontextmenü die Option **Member als Favorit** anheften aus.  Dadurch wird diese Eigenschaft an den Anfang der Eigenschaften Liste des Objekts hochskalieren, und der Eigenschaftsname und-Wert wird in der Spalte **Wert** angezeigt.  Wenn Sie eine Eigenschaft lösen möchten, wählen Sie das anheft Symbol erneut aus, oder wählen Sie im Kontextmenü die Option **Member als Favorit lösen** aus.

![Eigenschaften im Fenster "lokal" anheften](../debugger/media/basic-pin.gif "Eigenschaften im Fenster "lokal" anheften")

Wenn Sie die Eigenschaften Liste des Objekts in den Fenstern "Auto" oder "lokal" anzeigen, können Sie auch Eigenschaftsnamen umschalten und nicht fixierte Eigenschaften herausfiltern.  Sie können auf die einzelnen Optionen zugreifen, indem Sie die Schaltflächen auf der Symbolleiste oberhalb der Fenster Auto oder lokal auswählen.

![Filtern von Favoriten Eigenschaften](../debugger/media/filter-pinned-properties-locals.png "Favoriten Eigenschaften filtern")
![Umschalten von Eigenschaftsnamen](../debugger/media/toggle-property-names.gif "Eigenschaftsnamen umschalten")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Ändern des Kontexts für das Fenster "Auto" oder "lokal"

Sie können die Symbolleiste **Debugspeicherort** verwenden, um eine gewünschte Funktion, einen Thread oder einen Prozess auszuwählen, der **den Kontext** für das Fenster Auto und die **lokalen** Fenster ändert.

Um die Symbolleiste **Debugspeicherort** zu aktivieren, klicken Sie auf einen leeren Bereich der Symbolleiste, und **Wählen Sie in** der Dropdown Liste **Debugspeicherort** aus, oder wählen Sie > **Symbolleisten** > **Debugspeicherort**

Legen Sie einen Haltepunkt fest, und starten Sie das Debuggen. Wenn der Breakpoint gedrückt wird, wird die Ausführung angehalten, und Sie können den Speicherort auf der Symbolleiste **Debugspeicherort** sehen.

![Symbolleiste des Debug](../debugger/media/debuglocationtoolbar.png "Symbolleiste Debugspeicherort")

## <a name="bkmk_whatvariables"></a>Variablen im Fenster "Auto"C#( C++,, Visual Basic, python)

Verschiedene Code Sprachen zeigen verschiedene Variablen **im Fenster "** Auto" an.

- In C# und Visual Basic wird im Fenster **Auto** jede Variable angezeigt, die in der aktuellen oder vorherigen Zeile verwendet wird. Deklarieren Sie z C# . b. in oder Visual Basic Code die folgenden vier Variablen:

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   Legen Sie einen Haltepunkt auf der Zeilen `c = 3;`fest, und starten Sie den Debugger. Wenn **die Ausführung** angehalten wird, wird im Fenster Auto Folgendes angezeigt:

   ![Auto-CSharp](../debugger/media/autos-csharp.png "Autos-CSharp")

   Der Wert von `c` ist 0, da die Zeile `c = 3` noch nicht ausgeführt wurde.

- In C++werden im **Fenster Auto** die Variablen angezeigt, die in mindestens drei Zeilen vor der aktuellen Zeile verwendet werden, in der die Ausführung angehalten wurde. Deklarieren Sie z C++ . b. im Code sechs Variablen:

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    Legen Sie einen Haltepunkt in der Zeile `e = 5;`, und führen Sie den Debugger aus. Wenn **die Ausführung** beendet wird, wird im Fenster Auto Folgendes angezeigt:

    ![AutobauerC++](../debugger/media/autos-cplus.png "AutobauerC++")

    Die Variable `e` ist nicht initialisiert, da die Zeile `e = 5` noch nicht ausgeführt wurde.

## <a name="bkmk_returnValue"></a> View return values of method calls
 In .net und C++ Code können Sie Rückgabewerte im Fenster "Auto **" untersuchen** , wenn Sie einen Methoden aufrufschritt oder aus einem Prozedur Schritt ausführen. Das Anzeigen von Rückgabe Werten von Methoden aufrufen kann nützlich sein, wenn Sie nicht in lokalen Variablen gespeichert werden. Eine Methode kann als Parameter oder als Rückgabewert einer anderen Methode verwendet werden.

 Mit dem folgenden C# Code werden beispielsweise die Rückgabewerte von zwei Funktionen hinzugefügt:

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

So zeigen Sie die Rückgabewerte der `sumVars()` und `subtractVars()` Methodenaufrufe im Fenster "Auto" an:

1. Legen Sie einen Haltepunkt in der Zeile `int x = sumVars(a, b) + subtractVars(c, d);` fest.

1. Starten Sie das Debugging, und wenn die Ausführung am Haltepunkt angehalten wird, wählen Sie Prozedur **Schritt** aus, oder drücken Sie **F10**. Im **Fenster Auto sollten die folgenden** Rückgabewerte angezeigt werden:

  ![Auto-RückgabewertC#](../debugger/media/autosreturnvaluecsharp2.png "Auto-RückgabewertC#")

## <a name="see-also"></a>Siehe auch

- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Debugging techniques and tools (Debugverfahren und -tools)](../debugger/write-better-code-with-visual-studio.md)
- [Erster Einblick in das Debuggen](../debugger/debugger-feature-tour.md)
- [Debuggerfenster](../debugger/debugger-windows.md)

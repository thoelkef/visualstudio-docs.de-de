---
title: Untersuchen Sie Variablen – Fenster "Auto" und "lokal" | Microsoft-Dokumentation
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e23f61f7de4b2723e7be18b6beb76b17fd278cf2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947412"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Überprüfen von Variablen in den Fenstern "Auto" und "lokal"

Die **"Auto"** und **"lokal"** Windows zeigen Variablenwerte an, während des Debuggens. Die Windows sind nur verfügbar, während einer Debugsitzung. Die **"Auto"** Fenster zeigt die Variablen, die in der Nähe der aktuellen Haltepunkt verwendet. Die **"lokal"** Fenster zeigt die Variablen, die im lokalen Gültigkeitsbereich, in der Regel die aktuelle Funktion oder Methode definiert. Wenn dies das erste Mal, die Sie versucht haben ist, um Code zu debuggen, sollten Sie lesen [Beheben von Fehlern durch das Schreiben von besser C# Code](../debugger/write-better-code-with-visual-studio.md) und [Debuggen für absolute Anfänger](../debugger/debugging-absolute-beginners.md) , bevor Sie diesen Artikel durchgehen.

 Die **"Auto"** Fenster ist verfügbar für C#, Visual Basic, C++ und Python-Code, aber nicht für JavaScript oder F#.
  
Zum Öffnen der **"Auto"** wählen Sie im Fenster während des Debuggens **Debuggen** > **Windows** > **"Auto"**, oder drücken Sie **STRG**+**Alt**+**V** > **ein**.  

Zum Öffnen der **"lokal"** wählen Sie im Fenster während des Debuggens **Debuggen** > **Windows** > **"lokal"**, oder drücken Sie **Alt**+**4**.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Visual Studio für Mac finden Sie unter [datenvisualisierungen in Visual Studio für Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Verwenden Sie die Fenstern "Auto" und "lokal"

Anzeigen von Arrays und Objekten in der **"Auto"** und **"lokal"** Windows-as-Struktur-Steuerelemente. Wählen Sie den Pfeil links neben der Name einer Variablen um die Ansicht zum Anzeigen von Feldern und Eigenschaften erweitern. Hier ist ein Beispiel für eine <xref:System.IO.FileStream?displayProperty=fullName> -Objekt in der **"lokal"** Fenster:

!["Lokal" die FileStream-](../debugger/media/locals-filestream.png "\"lokal\" die FileStream-")

Ein Wert in der **"lokal"** oder **"Auto"** bedeutet der Wert wurde seit der letzten Auswertung geändert. Die Änderung möglicherweise aus einer vorherigen Debugsitzung stammen, oder weil Sie den Wert im Fenster geändert haben.

Das numerische Standardformat in Debuggerfenstern ist decimal. Auf das Hexadezimalformat ändern, mit der Maustaste in den **"lokal"** oder **"Auto"** Fenster, und wählen **Hexadezimale Anzeige**. Diese Änderung wirkt sich auf alle Debuggerfenster aus.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Bearbeiten Sie die Variablenwerte im Fenster "Auto" oder "lokal"

So bearbeiten Sie die Werte der meisten Variablen in der **"Auto"** oder **"lokal"** Windows-, doppelklicken Sie auf den Wert und geben Sie den neuen Wert.

Sie können Sie einen Ausdruck für einen Wert eingeben, etwa `a + b`. Der Debugger akzeptiert im die meisten gültigen Sprachausdrücke.

In nativem C++-Code müssen Sie möglicherweise den Kontext eines Variablennamens qualifizieren. Weitere Informationen finden Sie unter [Kontextoperator (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Stellen Sie sicher, dass Sie die Konsequenzen im Klaren sind, bevor Sie die Werte und Ausdrücke ändern. Mögliche Probleme sind:
>
>-   Die Auswertung bestimmter Ausdrücke kann zur Änderung des Werts einer Variablen führen oder sich auf den Programmzustand auswirken. Bewerten Sie z. B. `var1 = ++var2` ändert sich der Wert beider `var1` und `var2`. Diese Ausdrücke bewirken, haben [Nebeneffekte](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Nebeneffekte können unerwartete Ergebnisse verursacht werden, wenn Sie nicht bekannt sind.
>
>-   Das Bearbeiten von Gleitkommawerten kann aufgrund der Dezimal-zu-Binär-Konvertierung von Nachkommastellen zu geringfügigen Ungenauigkeiten führen. Auch eine scheinbar harmlose Bearbeitung kann Änderungen in einigen der Bits in einer Gleitkommavariable bewirken.

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Ändern Sie den Kontext für das Fenster "Auto" oder "lokal"

Können Sie die **Debugspeicherort** Symbolleiste wählen Sie die gewünschte Funktion, Thread oder Prozess, der den Kontext für die Änderungen der **"Auto"** und **"lokal"** Windows.

So aktivieren Sie die **Debugspeicherort** Symbolleiste, klicken Sie auf einen leeren Bereich der Symbolleiste, und wählen **Debugspeicherort** aus der Dropdownliste aus, oder wählen Sie **Ansicht**  >   **Symbolleisten** > **Debugspeicherort**.

Legen Sie einen Haltepunkt fest, und starten Sie das Debuggen. Wenn der Haltepunkt erreicht wird, Ausführung hält und Sie sehen die Position in der **Debugspeicherort** Symbolleiste.

![Symbolleiste "Debugspeicherort"](../debugger/media/debuglocationtoolbar.png "Symbolleiste Debugspeicherort")

## <a name="bkmk_whatvariables"></a> Variablen im Fenster "Auto" (C#, C++, Visual Basic, Python)

 Unterschiedliche Codesprachen zeigt verschiedene Variablen in der **"Auto"** Fenster.

 - In C# und Visual Basic wird im Fenster **Auto** jede Variable angezeigt, die in der aktuellen oder vorherigen Zeile verwendet wird. Z. B. in C# oder Visual Basic-code, deklarieren Sie die folgenden vier Variablen:

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

   Legen Sie einen Haltepunkt in der Zeile `c = 3;`, und starten Sie den Debugger. Wenn die Ausführung angehalten wird, die **"Auto"** Fenster angezeigt:

   ![Auto-CSharp](../debugger/media/autos-csharp.png "Auto-CSharp")

   Der Wert des `c` ist 0 (null), da die Zeile `c = 3` noch nicht ausgeführt wurde.

 - In C++ wird die **"Auto"** Fenster zeigt die Variablen, die in mindestens drei Zeilen vor der aktuellen Zeile verwendet werden, an dem die Ausführung angehalten wird. Zum Beispiel in C++-Code deklarieren Sie sechs Variablen:

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

    Legen Sie einen Haltepunkt in der Zeile `e = 5;` und den Debugger ausführen. Wenn die Ausführung anhält, der **"Auto"** Fenster angezeigt:

    !["Auto" – C++](../debugger/media/autos-cplus.png "\"Auto\" – C++")

    Die Variable `e` ist nicht initialisiert, da die Zeile `e = 5` noch nicht ausgeführt wurde.

##  <a name="bkmk_returnValue"></a> View return values of method calls
 In .NET und C++-Code können Sie überprüfen, Rückgabewerte in der **"Auto"** anzeigen, wenn Sie über eine oder aus einem Methodenaufruf schrittweise ausführen. Anzeigen der Methodenaufruf zurückgegeben, dass die Werte hilfreich sein können, wenn sie nicht in der lokalen Variablen gespeichert werden. Eine Methode kann als Parameter oder als Rückgabewert einer anderen Methode verwendet werden.

 Beispielsweise die folgenden C# Code fügt die Rückgabewerte von zwei Funktionen:

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

Um die Rückgabewerte der finden Sie unter den `sumVars()` und `subtractVars()` Methodenaufrufe im Fenster "Auto":

1. Legen Sie einen Haltepunkt in der Zeile `int x = sumVars(a, b) + subtractVars(c, d);` fest.  
   
1. Mit dem Debuggen beginnen, und wählen Sie bei der Ausführung am Haltepunkt angehalten wird, **Prozedurschritt** , oder drücken Sie **F10**. Daraufhin sollte die folgenden Rückgabewerte in der **"Auto"** Fenster:  
   
  !["Auto" Rückgabewert C# ](../debugger/media/autosreturnvaluecsharp2.png "Rückgabewert für \"Auto\"C#")  
  
## <a name="see-also"></a>Siehe auch  
 [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)  
 [Korrigieren von Fehlern durch das Schreiben von besserem C#-Code](../debugger/write-better-code-with-visual-studio.md)  
 [Ein erster Blick auf Debuggen](../debugger/debugger-feature-tour.md) [Debuggerfenster](../debugger/debugger-windows.md)

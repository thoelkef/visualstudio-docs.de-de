---
title: Suchen von Arbeits Speicherverlusten mit der CRT-Bibliothek | Microsoft-Dokumentation
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13a346aa0212f4830c2c88ed866b674fc19d30bd
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404981"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Finden von Arbeitsspeicherverlusten mit der CRT-Bibliothek

Speicher Verluste gehören zu den gängigsten und schwer zu erkennender Fehler in C/C++ apps. Arbeitsspeicher Verluste führen dazu, dass der zuvor zugewiesene Arbeitsspeicher nicht ordnungsgemäß freigegeben wird. Ein kleiner Speichermangel wird möglicherweise zuerst nicht bemerkt, aber im Laufe der Zeit kann es zu Symptomen zwischen einer schlechten Leistung und Abstürzen kommen, wenn die APP nicht über genügend Arbeitsspeicher verfügt. Eine Verlust-APP, die den gesamten verfügbaren Arbeitsspeicher beansprucht, kann dazu führen, dass andere apps abstürzen, wodurch Verwirrung entsteht, welche App verantwortlich ist. Sogar harmlose Speicher Verluste können auf andere Probleme hindeuten, die korrigiert werden sollten.

Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugger und die C-Lauf Zeit Bibliothek (CRT) können Ihnen helfen, Speicher Verluste zu erkennen und zu identifizieren.

## <a name="enable-memory-leak-detection"></a>Aktivieren der Erkennung von Speicherlecks

Die wichtigsten Tools zum Erkennen von Speicher Verlusten sind der cC++ /Debugger und die Debugheapfunktionen der c-Lauf Zeit Bibliothek (CRT).

Um alle Debugheapfunktionen zu aktivieren, fügen Sie C++ die folgenden Anweisungen in das Programm ein, und zwar in der folgenden Reihenfolge:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

Durch die `#define` -Anweisung wird eine Basisversion der CRT-Heapfunktionen der entsprechenden Debugversion zugeordnet. Wenn Sie die `#define`-Anweisung weglassen, wird der Speicher [Verlust weniger detailliert dargestellt](#interpret-the-memory-leak-report).

Durch das Einschließen von " *CRTDBG. h* " werden die `malloc`-und `free` Funktionen Ihren Debugversionen [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) und [_free_dbg](/cpp/c-runtime-library/reference/free-dbg)zugeordnet, die die Speicher Belegung und-Freigabe nachverfolgen. Diese Zuordnung findet nur in Debugbuilds mit `_DEBUG`statt. Releasebuilds verwenden die normalen Funktionen `malloc` und `free` .

Nachdem Sie die Debugheapfunktionen mithilfe der vorangehenden Anweisungen aktiviert haben, platzieren Sie [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) vor einem App-Beendigungs Punkt, um beim Beenden der APP einen Speicher ungenügenden Bericht anzuzeigen.

```cpp
_CrtDumpMemoryLeaks();
```

Wenn Ihre APP mehrere beenden hat, müssen Sie `_CrtDumpMemoryLeaks` nicht an jedem Endpunkt manuell platzieren. Wenn Sie einen automatischen `_CrtDumpMemoryLeaks` an jedem Endpunkt auslösen möchten, platzieren Sie `_CrtSetDbgFlag` am Anfang Ihrer APP mit den hier gezeigten Bitfeldern:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

Standardmäßig gibt `_CrtDumpMemoryLeaks` den Arbeitsspeicherverlust-Bericht im Bereich **Debuggen** des **Ausgabefensters** aus. Bei Verwendung einer Bibliothek wird die Ausgabe u. U. auf einen anderen Ort zurückgesetzt.

Sie können `_CrtSetReportMode` verwenden, um den Bericht an einen anderen Speicherort oder zurück zum **Ausgabe** Fenster umzuleiten, wie hier gezeigt:

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interpretieren des Arbeitsspeicher Lecks-Berichts

Wenn Ihre APP keine `_CRTDBG_MAP_ALLOC`definiert, zeigt [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) einen Arbeits speicherungenügbericht an, der wie folgt aussieht:

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Wenn Ihre APP `_CRTDBG_MAP_ALLOC`definiert, sieht der Arbeits speicherungenügbericht wie folgt aus:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Der zweite Bericht zeigt den Dateinamen und die Zeilennummer an, in der der kompromittierte Arbeitsspeicher zuerst zugewiesen wird.

Unabhängig davon, ob Sie `_CRTDBG_MAP_ALLOC`definieren, wird der Bericht "Speicherplatz" angezeigt:

- Die Speicher Belegungs Nummer, die im Beispiel `18` wird.
- Der Blocktyp, `normal` im Beispiel.
- Der hexadezimale Speicher Speicherort, `0x00780E80` im Beispiel.
- Die Größe des Blocks, `64 bytes` im Beispiel.
- Die ersten 16 Bytes Daten im Block im Hexadezimalformat

Speicherblock Typen sind *Normal*, *Client*oder *CRT*. Ein *normaler Block* ist gewöhnlicher, durch das Programm belegter Speicher. Ein *Clientblock* ist ein spezieller Speicherblocktyp, der von MFC-Programmen für Objekte verwendet wird, die einen Destruktor erfordern. Durch den MFC-Operator `new` wird entsprechend dem zu erstellenden Objekt ein normaler Block oder ein Clientblock erstellt.

Ein *CRT-Block* wird von der CRT-Bibliothek zur eigenen Verwendung belegt. Die CRT-Bibliothek behandelt die Aufhebung der Zuordnung für diese Blöcke, sodass CRT-Blöcke nicht im Arbeitsspeicher-ungenügendsten Bericht angezeigt werden, es sei denn, es sind schwerwiegende Probleme mit der CRT-Bibliothek

Zwei weitere Speicherblocktypen werden nie in Arbeitsspeicherverlust-Berichten angezeigt. Ein *freier Block* ist Speicher, der freigegeben wurde, sodass definitionsgemäß nicht verloren geht. Ein *Ignore-Block* ist der Arbeitsspeicher, den Sie explizit zum Ausschließen aus dem Arbeitsspeicher-ungenügende Bericht ausgewählt haben.

In den vorangehenden Verfahren werden Speicher Verluste für den Arbeitsspeicher identifiziert, der mithilfe der standardmäßigen CRT-`malloc` Funktion Wenn das Programmspeicher mithilfe des C++ `new`-Operators zuordnet, werden Ihnen möglicherweise nur der Dateiname und die Zeilennummer angezeigt, bei denen `operator new` Aufrufe `_malloc_dbg` im Arbeitsspeicher-ungenügwert melden. Zum Erstellen eines nützlicheren Speicherplatz Berichts können Sie ein Makro wie das folgende schreiben, um die Zeile zu melden, die die Zuordnung hergestellt hat:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Nun können Sie den `new`-Operator ersetzen, indem Sie das `DBG_NEW`-Makro in Ihrem Code verwenden. In Debugbuilds wird von `DBG_NEW` eine Überladung globaler `operator new` verwendet, die zusätzliche Parameter für den Blocktyp, die Datei und die Zeilennummer erfordert. Mit der Überladung von `new` werden `_malloc_dbg` aufgerufen, um die zusätzlichen Informationen aufzuzeichnen. In den Speicher Verlust Berichten werden der Dateiname und die Zeilennummer angezeigt, in der die kompromittierten Objekte zugeordnet wurden. Releasebuilds verwenden weiterhin die Standard `new`. Im folgenden finden Sie ein Beispiel für die Vorgehensweise:

```cpp
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```

Wenn Sie diesen Code im Visual Studio-Debugger ausführen, generiert der-`_CrtDumpMemoryLeaks` einen Bericht im **Ausgabe** Fenster, der in etwa wie folgt aussieht:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Diese Ausgabe meldet, dass die kompromittierte Zuordnung in Zeile 20 von *DEBUG_NEW. cpp*erfolgte.

>[!NOTE]
>Es wird nicht empfohlen, ein Präprozessormakro mit dem Namen `new`oder einem anderen sprach Schlüsselwort zu erstellen.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Festlegen von Haltepunkten für eine Speicher Belegungs Nummer

Die Speicherbelegungsnummer gibt Aufschluss darüber, wann ein Speicherblock mit Arbeitsspeicherverlust belegt wurde. Ein Block mit der Speicher Belegungs Nummer 18 ist z. b. der 18. Speicherblock, der während der APP-Laufzeit zugeordnet wird. Im CRT-Bericht werden alle Speicherblock Zuordnungen während des Testlaufs gezählt, einschließlich der Zuordnungen durch die CRT-Bibliothek und anderen Bibliotheken wie MFC. Daher ist die Speicher Belegungs Block Nummer 18 wahrscheinlich nicht der 18. Speicherblock, der von Ihrem Code zugewiesen wird.

Sie können die Speicherbelegungsnummer verwenden, um einen Haltepunkt für die Speicherbelegung festzulegen.

**So legen Sie einen Haltepunkt für die Speicherbelegung im Überwachungsfenster fest:**

1. Legen Sie einen Haltepunkt am Anfang der APP fest, und starten Sie das Debuggen.

1. Wenn die APP am Haltepunkt angehalten wird, öffnen **Sie ein Überwachungs** Fenster, indem Sie **Debuggen** > **Windows** > **Überwachung 1** (oder überwachen **2**, über **Wachen 3**oder überwachen **4**) auswählen.

1. Geben **Sie im Überwachungs** Fenster in der Spalte **Name** `_crtBreakAlloc` ein.

   Wenn Sie die Multithread-DLL-Version der CRT-Bibliothek (die/MD-Option) verwenden, fügen Sie den Kontext Operator hinzu: `{,,ucrtbased.dll}_crtBreakAlloc`
   
   Stellen Sie sicher, dass Debugsymbole geladen sind. Andernfalls wird `_crtBreakAlloc` als nicht *identifiziert*gemeldet.

1. Drücken Sie die **EINGABETASTE**.

   Der Debugger wertet den Aufruf aus und gibt das Ergebnis in der Spalte **Wert** aus. Wenn Sie keine Haltepunkte für Speicherbelegungen festgelegt haben, lautet dieser Wert **–1**.

1. Ersetzen Sie in der Spalte **Wert** den Wert durch die Zuordnungs Nummer der Speicher Belegung, in der der Debugger unterbrechen soll.

Nachdem Sie einen Haltepunkt für eine Speicher Belegungs Nummer festgelegt haben, fahren Sie mit dem Debuggen fort. Stellen Sie sicher, dass Sie unter denselben Bedingungen ausgeführt werden, sodass sich die Speicher Belegungs Nummer nicht ändert. Wenn das Programm bei der angegebenen Speicher Belegung unterbrochen wird, verwenden Sie das Fenster **"Fenster"** und andere Debuggerfenster, um die Bedingungen zu bestimmen, unter denen der Arbeitsspeicher zugeordnet wurde. Anschließend können Sie die Ausführung fortsetzen, um zu beobachten, was mit dem Objekt geschieht, und festzustellen, warum es nicht ordnungsgemäß freigegeben wird

Das Festlegen eines Datenhaltepunkts für das Objekt kann auch hilfreich sein. Weitere Informationen finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).

Sie können auch Speicherbelegungshaltepunkte im Code festlegen. Sie können folgende Einstellungen vornehmen:

```cpp
_crtBreakAlloc = 18;
```

 oder:

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Vergleichen von Arbeitsspeicher Zuständen

Ein weiteres Verfahren zum Ermitteln von Speicherverlusten besteht darin, zu bestimmten Zeitpunkten Momentaufnahmen von Speicherzuständen der Anwendung aufzuzeichnen. Um eine Momentaufnahme des Speicher Zustands an einem bestimmten Punkt in der Anwendung zu erstellen, erstellen Sie eine `_CrtMemState` Struktur, und übergeben Sie Sie an die Funktion `_CrtMemCheckpoint`.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

Die `_CrtMemCheckpoint`-Funktion füllt die-Struktur mit einer Momentaufnahme des aktuellen Speicher Zustands auf.

Um den Inhalt einer `_CrtMemState` Struktur auszugeben, übergeben Sie die-Struktur an die `_ CrtMemDumpStatistics`-Funktion:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` gibt ein Speicher Abbild des Speicher Zustands aus, das wie folgt aussieht:

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

Um festzustellen, ob in einem Codeabschnitt ein Arbeitsspeicherverlust aufgetreten ist, können Sie Momentaufnahmen des Speicherzustands vor und nach dem Abschnitt erstellen und die beiden Zustände anschließend mithilfe von `_ CrtMemDifference` vergleichen:

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference` vergleicht die Speicher Zustände `s1` und `s2` und gibt ein Ergebnis in (`s3`) zurück, bei dem es sich um den Unterschied zwischen `s1` und `s2`handelt.

Ein Verfahren zum Auffinden von Speicher Verlusten beginnt mit dem Platzieren von `_CrtMemCheckpoint`-aufrufen am Anfang und Ende der APP und der anschließenden Verwendung `_CrtMemDifference` zum Vergleichen der Ergebnisse. Wenn `_CrtMemDifference` einen Speicherlecks anzeigt, können Sie weitere `_CrtMemCheckpoint` Aufrufe hinzufügen, um das Programm mithilfe einer binären Suche aufzuteilen, bis Sie die Quelle des Lecks isoliert haben.

## <a name="false-positives"></a>Falsch positive Ergebnisse

 `_CrtDumpMemoryLeaks` kann falsche Anzeichen für Speicher Verluste verursachen, wenn eine Bibliothek Interne Zuordnungen als normale Blöcke anstelle von CRT-Blöcken oder Client Blöcken kennzeichnet. In diesem Fall kann `_CrtDumpMemoryLeaks` den Unterschied zwischen Benutzerspeicherbelegungen und internen Bibliotheksspeicherbelegungen nicht erkennen. Wenn die globalen Destruktoren für die Bibliotheksspeicherbelegungen nach dem Punkt ausgeführt werden, an dem `_CrtDumpMemoryLeaks`aufgerufen wird, wird jede interne Bibliotheksspeicherbelegung als Arbeitsspeicherverlust angezeigt. Versionen der Standard Vorlagen Bibliothek vor Visual Studio .net können `_CrtDumpMemoryLeaks` bewirken, dass diese falsch positiven Ergebnisse melden.

## <a name="see-also"></a>Siehe auch

- [Details zum CRT-Debugheap](../debugger/crt-debug-heap-details.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)

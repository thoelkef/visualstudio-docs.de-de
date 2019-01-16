---
title: Suche nach Speicherverlusten mit der CRT-Bibliothek | Microsoft-Dokumentation
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e29ef610fdfe114525e7da22b58635e0f3e4a3af
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931026"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Finden von Arbeitsspeicherverlusten mit der CRT-Bibliothek

Speicherverluste gehören zu den kleinen und schwierig zu erkennenden Fehlern in C/C++-apps. Arbeitsspeicherverluste Ergebnis nach dem Fehler um ordnungsgemäß Arbeitsspeicher freizugeben, der zuvor zugewiesen wurde. Ein geringfügiger Speicherverlust möglicherweise zuerst nicht bemerkt werden, aber im Laufe der Zeit Symptome, die von einer schlechten Leistung bis hin zu Abstürzen bei der Ausführung der app nicht genügend Arbeitsspeicher verursachen. Ein Verlust app, die verwendet, um den gesamten verfügbaren Arbeitsspeicher auf andere apps zum Absturz verursachen können, ist das Erstellen von Verwirrung in Bezug auf die app verantwortlich. Sogar harmlose Arbeitsspeicherverluste möglicherweise andere Probleme, die korrigiert werden sollten.  

 Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugger und die C Run-Time-Laufzeitbibliothek (CRT) können Sie erkennen und Identifizieren von Arbeitsspeicherverlusten.  

## <a name="enable-memory-leak-detection"></a>Aktivieren der speicherverlusterkennung  

Die wichtigsten Tools zum Feststellen von Speicherverlusten der C/C++-Debugger und die C-Laufzeit-Laufzeitbibliothek (CRT) Debugheapfunktionen an.  

Um alle die Debugheapfunktionen zu aktivieren, fügen Sie die folgenden Anweisungen im C++-Programm, in der folgenden Reihenfolge aus:  

```cpp
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  

Durch die `#define` -Anweisung wird eine Basisversion der CRT-Heapfunktionen der entsprechenden Debugversion zugeordnet. Wenn Sie sich lassen die `#define` -Anweisung das Speicherabbild des Arbeitsspeicherverlusts werden [weniger detaillierte](#interpret-the-memory-leak-report).  

Einschließlich *"CRTDBG.h"* ordnet die `malloc` und `free` Funktionen, um den entsprechenden Debugversionen [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) und [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), Nachverfolgen von Arbeitsspeicher Zuordnung und Aufhebung der Zuordnung. Diese Zuordnung findet nur in Debugbuilds mit `_DEBUG`statt. Releasebuilds verwenden die normalen Funktionen `malloc` und `free` .  

Nachdem Sie die Debugheapfunktionen mit den obigen Anweisungen aktiviert haben, legen Sie einen Aufruf von [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) vor dem Endpunkt eine app zu einen Arbeitsspeicherverlust-Bericht angezeigt wird, wenn die app wird beendet.  

```cpp
_CrtDumpMemoryLeaks();  
```  

Wenn Ihre app mehrere Endpunkte verfügt, müssen Sie nicht manuell `_CrtDumpMemoryLeaks` an jedem Endpunkt. Zu einen automatischen Aufruf von führen `_CrtDumpMemoryLeaks` zu jedem Zeitpunkt beenden, platzieren Sie einen Aufruf von `_CrtSetDbgFlag` am Anfang Ihrer app mit den hier gezeigten Bitfelder:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  

Standardmäßig gibt `_CrtDumpMemoryLeaks` den Arbeitsspeicherverlust-Bericht im Bereich **Debuggen** des **Ausgabefensters** aus. Bei Verwendung einer Bibliothek wird die Ausgabe u. U. auf einen anderen Ort zurückgesetzt. 

Können Sie `_CrtSetReportMode` auf den Bericht an einen anderen Speicherort umleiten oder zurück an die **Ausgabe** wie hier gezeigt:  

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  

## <a name="interpret-the-memory-leak-report"></a>Interpretieren des Arbeitsspeicherverlust Bericht  

Wenn Ihre app definieren nicht `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) zeigt einen Arbeitsspeicherverlust-Bericht, die wie folgt aussieht:  

```cmd
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

Wenn Ihre app definiert `_CRTDBG_MAP_ALLOC`, sieht der Arbeitsspeicherverlust Bericht:  

```cmd
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

Der zweite Bericht zeigt die Anzahl von Dateinamen und Zeilennummern, in dem für der Arbeitsspeicherverlust zuerst belegt wird.  

Sie definieren, ob `_CRTDBG_MAP_ALLOC`, im Arbeitsspeicherverlust-Bericht wird angezeigt:  

- Die Speicherbelegungsnummer, handelt es sich `18` im Beispiel  
- Der Blocktyp `normal` im Beispiel.  
- Der hexadezimale Speicherbereich `0x00780E80` im Beispiel.  
- Die Größe des Blocks `64 bytes` im Beispiel.  
- Die ersten 16 Bytes Daten im Block im Hexadezimalformat  

Arbeitsspeicher-Typen sind *normalen*, *Client*, oder *CRT*. Ein *normaler Block* ist gewöhnlicher, durch das Programm belegter Speicher. Ein *Clientblock* ist ein spezieller Speicherblocktyp, der von MFC-Programmen für Objekte verwendet wird, die einen Destruktor erfordern. Durch den MFC-Operator `new` wird entsprechend dem zu erstellenden Objekt ein normaler Block oder ein Clientblock erstellt. 

Ein *CRT-Block* wird von der CRT-Bibliothek zur eigenen Verwendung belegt. Die CRT-Bibliothek behandelt die Freigabe der speicherbelegung für diese Blöcke, damit die CRT-Blöcke nicht im Arbeitsspeicherverlust-Bericht angezeigt, es sei denn, es schwerwiegende Probleme mit der CRT-Bibliothek gibt.  

Zwei weitere Speicherblocktypen werden nie in Arbeitsspeicherverlust-Berichten angezeigt. Ein *freier Block* Arbeitsspeicher, der freigegeben wurde damit definitionsgemäß nicht ist, ist. Ein *ignorierter Block* Arbeitsspeicher, die Ihnen explizit markiert haben, damit vom Arbeitsspeicherverlust-Bericht ausgeschlossen wird.  

Die vorangehenden Verfahren zu identifizieren, Speicherverluste für speicherbelegung mithilfe der CRT `malloc` Funktion. Wenn Ihr Programm Speicher mithilfe des C++ zuordnet `new` -Operator, allerdings können nur sehen Sie die Anzahl von Dateinamen und Zeilennummern, in denen `operator new` Aufrufe `_malloc_dbg` im Arbeitsspeicherverlust-Bericht. Um eine nützlichere Arbeitsspeicherverlust-Bericht zu erstellen, können Sie schreiben ein Makro wie folgt auf die Zeile zu melden, die die Reservierung durchgeführt: 

```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  

Nun können Sie ersetzen die `new` Operator mithilfe der `DBG_NEW` Makro in Ihrem Code. In Debugbuilds `DBG_NEW` verwendet eine Überladung der globalen `operator new` , akzeptiert zusätzliche Parameter für den Blocktyp, Datei und Zeilennummer. Die Überladung von `new` Aufrufe `_malloc_dbg` , die zusätzliche Informationen zu erfassen. Der Arbeitsspeicherverlust-Berichten zeigen die Anzahl von Dateinamen und Zeilennummern, in denen der kompromittierte Objekte reserviert wurden. Releasebuilds verwenden weiterhin Standard `new`. Hier ist ein Beispiel dieser Methode:  

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

Beim Ausführen dieses Codes in Visual Studio-debugger, den Aufruf von `_CrtDumpMemoryLeaks` generiert einen Bericht in der **Ausgabe** Fenster, das so aussieht:  

```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  

Diese Ausgabe meldet, dass die kompromittierte Zuordnung in Zeile 20 des war *debug_new.cpp*.  

>[!NOTE]
>Nicht empfohlen, Sie erstellen ein Präprozessormakro mit dem Namen `new`, oder andere Programmiersprachen-Schlüsselwort. 

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Festlegen von Breakpoints für eine Speicherbelegungsnummer  

Die Speicherbelegungsnummer gibt Aufschluss darüber, wann ein Speicherblock mit Arbeitsspeicherverlust belegt wurde. Ein Block mit der Speicherbelegungsnummer 18 ist z. B. der 18. Speicherblock, der während der Ausführung der app zugeordnet. Die CRT-Bericht werden alle speicherblockbelegungen während der Ausführung, einschließlich der speicherbelegungen durch die CRT-Bibliothek und anderen Bibliotheken wie MFC zählt. Deshalb keine Arbeitsspeicher Block Speicherbelegungsnummer 18 möglicherweise der 18. Speicherblock, der von Ihrem Code belegt. 

Sie können die Speicherbelegungsnummer verwenden, um einen Haltepunkt für die Speicherbelegung festzulegen.  

**So legen Sie einen Haltepunkt für die Speicherbelegung im Überwachungsfenster fest:**  

1. Legen Sie einen Haltepunkt am Anfang Ihrer app, und starten Sie das Debuggen.  
   
1. Wenn Sie die app am Haltepunkt angehalten wird, öffnen Sie eine **Watch** Fenster durch Auswahl **Debuggen** > **Windows** > **Überwachen 1** (oder **Überwachen 2**, **Überwachen 3**, oder **Überwachen 4**).  
   
1. In der **Watch** geben `_crtBreakAlloc` in die **Namen** Spalte.  
   
   Bei Verwendung die Multithread-DLL-Version der CRT-Bibliothek (/ MD-Option), fügen Sie den Kontextoperator ein: `{,,ucrtbased.dll}_crtBreakAlloc`  
   
1. Drücken Sie die **EINGABETASTE**.  
   
   Der Debugger wertet den Aufruf aus und gibt das Ergebnis in der Spalte **Wert** aus. Wenn Sie keine Haltepunkte für Speicherbelegungen festgelegt haben, lautet dieser Wert **–1**.  
   
1. In der **Wert** Spalte, ersetzen Sie den Wert durch die Speicherbelegungsnummer der speicherbelegung, in denen den Debugger unterbrochen werden sollen.  

Nachdem Sie einen Haltepunkt für eine Speicherbelegungsnummer festgelegt, wird um das Debuggen fortzusetzen. Stellen Sie sicher, dass unter gleichen Bedingungen ausgeführt werden, damit die Speicherbelegungsnummer nicht ändert. Wenn das Programm bei der angegebenen speicherbelegung unterbrochen wird, verwenden Sie die **Aufrufliste** Fenster und anderen Debuggerfenstern überprüfen Bedingungen, unter dem der Speicher belegt wurde. Anschließend können Sie Ausführung fortsetzen, um zu sehen, was dem Objekt geschieht und bestimmen, warum sie ordnungsgemäß freigegeben ist nicht.  

Das Festlegen eines Datenhaltepunkts für das Objekt kann auch hilfreich sein. Weitere Informationen finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).  

Sie können auch Speicherbelegungshaltepunkte im Code festlegen. Sie können folgende Einstellungen vornehmen:  

```cpp
_crtBreakAlloc = 18;  
```  

 oder:  

```cpp
_CrtSetBreakAlloc(18);  
```  

## <a name="compare-memory-states"></a>Speicherzustände verglichen werden soll  
 Ein weiteres Verfahren zum Ermitteln von Speicherverlusten besteht darin, zu bestimmten Zeitpunkten Momentaufnahmen von Speicherzuständen der Anwendung aufzuzeichnen. Um eine Momentaufnahme des Speicherzustands an einem bestimmten Punkt in Ihrer Anwendung zu erstellen, erstellen Sie eine `_CrtMemState` Struktur, und übergeben es an der `_CrtMemCheckpoint` Funktion. 

```cpp
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
```  

Die `_CrtMemCheckpoint` Funktion, die in der Struktur mit einer Momentaufnahme des aktuellen Speicherzustands füllt.  

Um den Inhalt der Ausgabe ein `_CrtMemState` strukturieren, übergeben Sie die Struktur, die die `_ CrtMemDumpStatistics` Funktion:  

```cpp
_CrtMemDumpStatistics( &s1 );  
```  

`_ CrtMemDumpStatistics` Gibt ein Speicherabbild des Speicherzustands aus, die wie folgt aussieht:  

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

`_CrtMemDifference` Vergleicht die Speicherzustände `s1` und `s2` und ein Ergebnis in zurückgibt (`s3`), den Unterschied zwischen `s1` und `s2`.  

Ein Verfahren zum Suchen von Arbeitsspeicherverlusten beginnt, mit dem Platzieren von `_CrtMemCheckpoint` Aufrufe am Anfang und Ende Ihrer-app, klicken Sie dann mit `_CrtMemDifference` , die Ergebnisse verglichen werden soll. Wenn `_CrtMemDifference` zeigt einem Arbeitsspeicherverlust können Sie weitere hinzufügen `_CrtMemCheckpoint` Aufrufe, Teilen Ihr Programm mit einer Binärsuche, bis Sie die Quelle des Verlusts isoliert haben.  

## <a name="false-positives"></a>Falsch positive Ergebnisse  
 `_CrtDumpMemoryLeaks` erhalten falsche Angaben zu Speicherverlusten, wenn eine Bibliothek interne Zuordnungen als normale Blöcke anstelle von CRT-Blöcke oder Client blockiert markiert ist. In diesem Fall kann `_CrtDumpMemoryLeaks` den Unterschied zwischen Benutzerspeicherbelegungen und internen Bibliotheksspeicherbelegungen nicht erkennen. Wenn die globalen Destruktoren für die Bibliotheksspeicherbelegungen nach dem Punkt ausgeführt werden, an dem `_CrtDumpMemoryLeaks`aufgerufen wird, wird jede interne Bibliotheksspeicherbelegung als Arbeitsspeicherverlust angezeigt. Versionen vor Visual Studio .NET kann dazu führen, dass die Standard Template Library `_CrtDumpMemoryLeaks` , solche falschen Positivdiagnosen.  

## <a name="see-also"></a>Siehe auch  
 [Details zum CRT-Debugheap](../debugger/crt-debug-heap-details.md)   
 [Debugger security (Debuggersicherheit)](../debugger/debugger-security.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)

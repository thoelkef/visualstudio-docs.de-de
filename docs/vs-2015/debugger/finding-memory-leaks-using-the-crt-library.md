---
title: Suchen von Arbeitsspeicherverlusten mit der CRT-Bibliothek | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d2c45ed2377b400fb00ac264aa2dcf8e5df8410
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879771"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Suchen von Arbeitsspeicherverlusten mit der CRT-Bibliothek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [suchen Arbeitsspeicher Ressourcenlecks mithilfe der CRT-Bibliothek](https://docs.microsoft.com/visualstudio/debugger/finding-memory-leaks-using-the-crt-library).  
  
Arbeitsspeicherverluste (definiert als Fehler beim korrekten Freigeben einer zuvor vorgenommenen Speicherbelegung) zählen zu den heikelsten und am schwierigsten zu erkennenden Fehlern in C/C++-Anwendungen. Ein kleiner Arbeitsspeicherverlust würde möglicherweise zuerst nicht bemerkt werden. Im Laufe der Zeit kann ein fortschreitender Arbeitsspeicherverlust jedoch Symptome verursachen, die von verringerter Leistung bis hin zu einem Absturz reichen, wenn der Anwendung kein Arbeitsspeicher mehr zur Verfügung steht. Schwerwiegender ist hierbei jedoch, dass eine Anwendung mit Arbeitsspeicherverlusten, die den gesamten verfügbaren Arbeitsspeicher aufbraucht, einen Absturz anderer Anwendungen verursachen kann, wodurch das Identifizieren der für den Fehler verantwortlichen Anwendung erschwert wird. Auch scheinbar harmlose Arbeitsspeicherverluste können ein Symptom für andere Probleme sein, die korrigiert werden sollten.  
  
 Der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debugger und die C-Laufzeitbibliotheken (CRT) enthalten die notwendigen Mittel zum Erkennen und Identifizieren von Arbeitsspeicherverlusten.  
  
## <a name="enabling-memory-leak-detection"></a>Aktivieren der Speicherverlusterkennung  
 Die wichtigsten Tools zum Feststellen von Speicherverlusten sind der Debugger und die Debugheapfunktionen der C-Laufzeitbibliotheken.  
  
 Um die Debugheapfunktionen zu aktivieren, fügen Sie die folgenden Anweisungen in das Programm ein:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Damit die CRT ordnungsgemäß funktioniert, müssen die `#include` -Anweisungen in der hier gezeigten Reihenfolge angegeben werden.  
  
 Durch Verwendung von "crtdbg.h" werden die `malloc` - und [free](http://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) -Funktionen den entsprechenden Debugversionen [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) und `free`zugeordnet, die die Speicherbelegung und -freigabe nachverfolgen. Diese Zuordnung findet nur in Debugbuilds mit `_DEBUG`statt. Releasebuilds verwenden die normalen Funktionen `malloc` und `free` .  
  
 Durch die `#define` -Anweisung wird eine Basisversion der CRT-Heapfunktionen der entsprechenden Debugversion zugeordnet. Wenn Sie die `#define` -Anweisung weglassen, ist das Speicherabbild des Arbeitsspeicherverlusts weniger detailliert.  
  
 Nachdem Sie die Debugheapfunktionen mit diesen Anweisungen aktiviert haben, können Sie einen Aufruf von `_CrtDumpMemoryLeaks` vor einem Anwendungsendpunkt einfügen, damit beim Beenden der Anwendung ein Arbeitsspeicherverlust-Bericht angezeigt wird:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Wenn die Anwendung über mehrere Endpunkte verfügt, ist es nicht erforderlich, manuell einen Aufruf von [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) an jedem Endpunkt einzufügen. Ein Aufruf von `_CrtSetDbgFlag` am Anfang der Anwendung führt zu einem automatischen Aufruf von `_CrtDumpMemoryLeaks` an jedem Endpunkt. Die beiden Bitfelder müssen wie hier dargestellt festgelegt werden:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Standardmäßig gibt `_CrtDumpMemoryLeaks` den Arbeitsspeicherverlust-Bericht im Bereich **Debuggen** des **Ausgabefensters** aus. Sie können `_CrtSetReportMode` verwenden, um den Bericht an einen anderen Ort umzuleiten.  
  
 Bei Verwendung einer Bibliothek wird die Ausgabe u. U. auf einen anderen Ort zurückgesetzt. In diesem Fall können Sie den Ausgabeort wie hier dargestellt wieder auf das **Ausgabefenster** festlegen:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interpretieren des Arbeitsspeicherverlust-Berichts  
 Wenn `_CRTDBG_MAP_ALLOC`nicht in der Anwendung definiert ist, zeigt [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) einen Arbeitsspeicherverlust-Bericht an, der wie folgt aussieht:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Wenn `_CRTDBG_MAP_ALLOC`in der Anwendung definiert ist, sieht der Arbeitsspeicherverlust-Bericht wie folgt aus:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Der Unterschied besteht darin, dass der zweite Bericht den Namen der Datei und die Zeilennummer enthält, in der der Speicherblock mit dem Arbeitsspeicherverlust zuerst belegt wurde.  
  
 Unabhängig davon, ob Sie `_CRTDBG_MAP_ALLOC` definieren, werden die folgenden Informationen im Arbeitsspeicherverlust-Bericht angezeigt:  
  
-   Die Speicherbelegungsnummer (in diesem Beispiel `18` )  
  
-   Der [Blocktyp](http://msdn.microsoft.com/en-us/e2f42faf-0687-49e7-aa1f-916038354f97)(in diesem Beispiel `normal` )  
  
-   Der hexadezimale Speicherbereich (in diesem Beispiel `0x00780E80` )  
  
-   Die Größe des Blocks (in diesem Beispiel `64 bytes` )  
  
-   Die ersten 16 Bytes Daten im Block im Hexadezimalformat  
  
 Im Arbeitsspeicherverlust-Bericht wird ein Speicherblock als normaler Block, Clientblock oder CRT-Block angegeben. Ein *normaler Block* ist gewöhnlicher, durch das Programm belegter Speicher. Ein *Clientblock* ist ein spezieller Speicherblocktyp, der von MFC-Programmen für Objekte verwendet wird, die einen Destruktor erfordern. Durch den MFC-Operator `new` wird entsprechend dem zu erstellenden Objekt ein normaler Block oder ein Clientblock erstellt. Ein *CRT-Block* wird von der CRT-Bibliothek zur eigenen Verwendung belegt. Die CRT-Bibliothek behandelt die Freigabe der Speicherbelegung für diese Blöcke. Daher werden diese Blöcke nur dann im Arbeitsspeicherverlust-Bericht angezeigt, wenn ein bedeutender Fehler vorliegt, z. B. eine Beschädigung der CRT-Bibliothek.  
  
 Zwei weitere Speicherblocktypen werden nie in Arbeitsspeicherverlust-Berichten angezeigt. Ein *freier Block* ist ein Speicherblock, der freigegeben wurde. Dies bedeutet definitionsgemäß, dass kein Verlust vorliegt. Ein *ignorierter Block* ist ein Speicherblock, der von Ihnen explizit markiert wurde, damit er vom Arbeitsspeicherverlust-Bericht ausgeschlossen wird.  
  
 Diese Methoden funktionieren für Speicher, der mithilfe der CRT-Standardfunktion `malloc` belegt wird. Wenn Ihr Programm Speicher mithilfe des C++ zuordnet `new` -Operator, allerdings können nur sehen Sie die Anzahl und die Zeilennummer, in denen die Implementierung der globalen `operator new` Aufrufe `_malloc_dbg` im Arbeitsspeicherverlust-Bericht. Da dieses Verhalten nicht sehr nützlich ist, können Sie ändern, um die Zeile zu melden, die die Zuordnung vorgenommen, mit der ein Makro, das wie folgt aussieht: 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Nun können Sie ersetzen die `new` Operator mithilfe der `DBG_NEW` Makro in Ihrem Code. In Debugbuilds, verwendet es sich hierbei um eine Überladung der globalen `operator new` , akzeptiert zusätzliche Parameter für den Blocktyp, Datei und Zeilennummer. Diese Überladung der `new` Aufrufe `_malloc_dbg` , die zusätzliche Informationen zu erfassen. Bei Verwendung von `DBG_NEW`, der Speicherverlust Berichte zeigen die Anzahl von Dateinamen und Zeilennummern, in denen der kompromittierte Objekte reserviert wurden. In Verkaufsversionen, verwendet dieser den Standardwert `new`. (Es wird nicht empfohlen, Sie erstellen ein Präprozessormakro mit dem Namen `new`, oder andere Programmiersprachen-Schlüsselwort.) Hier ist ein Beispiel dieser Methode:  
  
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
  
Wenn Sie diesen Code im Debugger in Visual Studio, den Aufruf ausführen `_CrtDumpMemoryLeaks` generiert einen Bericht in der **Ausgabe** Fenster, das etwa wie folgt aussieht:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Dadurch sehen Sie, dass die kompromittierte Zuordnung in Zeile 20 des debug_new.cpp war.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Festlegen von Haltepunkten für eine Speicherbelegungsnummer  
 Die Speicherbelegungsnummer gibt Aufschluss darüber, wann ein Speicherblock mit Arbeitsspeicherverlust belegt wurde. Ein Block mit der Speicherbelegungsnummer 18 ist z. B. der 18. Speicherblock, der während der Ausführung der Anwendung belegt wurde. Im CRT-Bericht werden alle Speicherblockbelegungen während der Ausführung gezählt. Dies beinhaltet Speicherbelegungen von der CRT-Bibliothek und anderen Bibliotheken wie MFC. Daher ist ein Block mit der Speicherbelegungsnummer 18 möglicherweise nicht der 18. Speicherblock, der von Ihrem Code belegt wurde. In der Regel ist dies nicht der Fall.  
  
 Sie können die Speicherbelegungsnummer verwenden, um einen Haltepunkt für die Speicherbelegung festzulegen.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>So legen Sie einen Haltepunkt für die Speicherbelegung im Überwachungsfenster fest  
  
1.  Legen Sie am Anfang der Anwendung einen Haltepunkt fest, und starten Sie dann die Anwendung.  
  
2.  Wenn die Anwendung am Haltepunkt unterbrochen wird, wird das **Überwachungsfenster** angezeigt.  
  
3.  In der **Watch** geben `_crtBreakAlloc` in die **Namen** Spalte.  
  
     Bei Verwendung der Multithread-DLL-Version der CRT-Bibliothek (/MD-Option) schließen Sie den Kontextoperator ein: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4.  Drücken Sie die **EINGABETASTE**.  
  
     Der Debugger wertet den Aufruf aus und gibt das Ergebnis in der Spalte **Wert** aus. Wenn Sie keine Haltepunkte für Speicherbelegungen festgelegt haben, lautet dieser Wert –1.  
  
5.  Ersetzen Sie den angezeigten Wert in der Spalte **Wert** durch die Speicherbelegungsnummer, bei der die Unterbrechung erfolgen soll.  
  
 Nachdem Sie einen Haltepunkt für eine Speicherbelegungsnummer festgelegt haben, können Sie mit dem Debuggen fortfahren. Das Programm muss unter denselben Bedingungen wie zuvor ausgeführt werden, damit die Speicherbelegung in derselben Reihenfolge erfolgt. Wenn das Programm bei der angegebenen Speicherbelegung unterbrochen wird, können Sie im Fenster **Aufrufliste** und in anderen Debuggerfenstern überprüfen, unter welchen Bedingungen der Speicher belegt wurde. Anschließend können Sie die Ausführung fortsetzen, um zu beobachten, was mit dem Objekt geschieht, und festzustellen, warum es nicht ordnungsgemäß freigegeben wird.  
  
 Das Festlegen eines Datenhaltepunkts für das Objekt kann auch hilfreich sein. Weitere Informationen finden Sie unter [Using Breakpoints](../debugger/using-breakpoints.md).  
  
 Sie können auch Speicherbelegungshaltepunkte im Code festlegen. Hierfür gibt es zwei Möglichkeiten:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 oder:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Vergleichen von Arbeitsspeicherzuständen  
 Ein weiteres Verfahren zum Ermitteln von Speicherverlusten besteht darin, zu bestimmten Zeitpunkten Momentaufnahmen von Speicherzuständen der Anwendung aufzuzeichnen. Um eine Momentaufnahme des Speicherzustands an einem bestimmten Punkt in der Anwendung aufzuzeichnen, erstellen Sie eine **_CrtMemState** -Struktur, die Sie dann an die `_CrtMemCheckpoint` -Funktion übergeben. Durch diese Funktion wird eine Momentaufnahme des aktuellen Speicherzustands in die Struktur eingefügt:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` fügt eine Momentaufnahme des aktuellen Speicherzustands in die Struktur ein.  
  
 Um den Inhalt einer **_CrtMemState** -Struktur auszugeben, übergeben Sie sie an die `_ CrtMemDumpStatistics` -Funktion:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` gibt ein Speicherabbild des Speicherzustands aus, das wie folgt aussieht:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Um festzustellen, ob in einem Codeabschnitt ein Arbeitsspeicherverlust aufgetreten ist, können Sie Momentaufnahmen des Speicherzustands vor und nach dem Abschnitt erstellen und die beiden Zustände anschließend mithilfe von `_ CrtMemDifference` vergleichen:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` vergleicht die Speicherzustände `s1` und `s2` und gibt in (`s3`) ein Ergebnis zurück, das die Differenz zwischen `s1` und `s2`darstellt.  
  
 Eine Methode zur Suche nach Arbeitsspeicherverlusten besteht darin, zunächst `_CrtMemCheckpoint`-Aufrufe am Anfang und Ende der Anwendung einzufügen und anschließend mit `_CrtMemDifference` die Ergebnisse zu vergleichen. Wenn `_CrtMemDifference` einen Arbeitsspeicherverlust anzeigt, können Sie weitere `_CrtMemCheckpoint` -Aufrufe hinzufügen, um das Programm anhand einer Binärsuche aufzuteilen, bis Sie die Quelle des Verlusts gefunden haben.  
  
## <a name="false-positives"></a>Falsch positive Ergebnisse  
 In manchen Fällen kann `_CrtDumpMemoryLeaks` falsche Angaben zu Speicherverlusten machen. Dies kann bei Verwendung einer Bibliothek vorkommen, die interne Speicherbelegungen nicht als `_CRT_BLOCK`s oder `_CLIENT_BLOCK`s markiert, sondern als _NORMAL_BLOCKs. In diesem Fall kann `_CrtDumpMemoryLeaks` den Unterschied zwischen Benutzerspeicherbelegungen und internen Bibliotheksspeicherbelegungen nicht erkennen. Wenn die globalen Destruktoren für die Bibliotheksspeicherbelegungen nach dem Punkt ausgeführt werden, an dem `_CrtDumpMemoryLeaks`aufgerufen wird, wird jede interne Bibliotheksspeicherbelegung als Arbeitsspeicherverlust angezeigt. In früheren Versionen der Standardvorlagenbibliothek (vor Visual Studio .NET) wurden solche falsch positiven Ergebnisse von `_CrtDumpMemoryLeaks` ausgegeben, in neueren Versionen wurde dies jedoch behoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Details zum CRT-Debugbibliothek-Debugheap](../debugger/crt-debug-heap-details.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)




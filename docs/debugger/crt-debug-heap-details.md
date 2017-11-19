---
title: CRT Debug Heap Details | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 947da9ccdbf67a71edfaa122de8861912a9e9596
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="crt-debug-heap-details"></a>Details zum CRT-Debugheap
Dieses Thema umfasst eine detaillierte Erläuterung des CRT‑Debugheaps.  
  
##  <a name="BKMK_Contents"></a> Inhalt  
 [Suchen von Pufferüberläufen mit Debugheap](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Blocktypen auf dem Debugheap](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Überprüfen Sie auf Heapintegrität und Speicherverluste](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Konfigurieren des Debugheap](#BKMK_Configure_the_debug_heap)  
  
 [neue Debugheap löschen und _CLIENT_BLOCKs im C++](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Für den Heapzustand](#BKMK_Heap_State_Reporting_Functions)  
  
 [Nachverfolgen von Heapreservierungsanforderungen](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a>Suchen von Pufferüberläufen mit Debugheap  
 Zwei der geläufigsten und hartnäckigsten Probleme, denen sich Programmierer immer wieder gegenüber sehen, ist das Überschreiben eines reservierten Pufferendes und Speicherverluste (wobei die Freigabe der nicht mehr benötigten Belegung fehlschlägt). Der Debugheap stellt leistungsfähige Tools bereit, die derartige Speicherbelegungsprobleme beheben helfen.  
  
 Durch die Debugversionen der Heapfunktionen wird die Standard- oder Basisversion aufgerufen, die in Releasebuilds verwendet wird. Wenn Sie einen Speicherblock anfordern, belegt der Debugheap-Manager auf dem Basisheap einen Speicherblock, der geringfügig größer als der angeforderte ist, und gibt einen Zeiger auf den jeweiligen Bereich des Blocks zurück. Angenommen, die Anwendung enthält den `malloc( 10 )`-Aufruf. In einem Releasebuild ["malloc"](/cpp/c-runtime-library/reference/malloc) würde eine Reservierung von 10 Bytes anfordern Basisheap Zuweisung Routine aufrufen. In einem Debugbuild jedoch `malloc` aufrufen würde [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg), die aufrufen würde dann der Basisheap Zuweisung Routine eine Reservierung von 10 Bytes sowie etwa 36 Bytes zusätzlicher Speicher angefordert. Alle resultierenden Speicherblöcke im Debugheap werden über eine einzelne verknüpfte Liste verbunden und sind nach ihrem Reservierungszeitpunkt angeordnet.  
  
 Der durch die Debugheaproutinen belegte Zusatzspeicher wird wie folgt verwendet: für Verwaltungsinformationen, für Zeiger, die die Debugspeicherblöcke verknüpfen, und für kleine Puffer auf beiden Seiten der Daten, um Überschreibungen des reservierten Bereichs abzufangen.  
  
 Derzeit ist die zum Speichern der Debugheap-Verwaltungsinformationen verwendete Blockheaderstruktur wie folgt in der Headerdatei DBGINT.H deklariert:  
  
```  
typedef struct _CrtMemBlockHeader  
{  
// Pointer to the block allocated just before this one:  
    struct _CrtMemBlockHeader *pBlockHeaderNext;  
// Pointer to the block allocated just after this one:  
    struct _CrtMemBlockHeader *pBlockHeaderPrev;  
    char *szFileName;    // File name  
    int nLine;           // Line number  
    size_t nDataSize;    // Size of user block  
    int nBlockUse;       // Type of block  
    long lRequest;       // Allocation number  
// Buffer just before (lower than) the user's memory:  
    unsigned char gap[nNoMansLandSize];  
} _CrtMemBlockHeader;  
  
/* In an actual memory block in the debug heap,  
 * this structure is followed by:  
 *   unsigned char data[nDataSize];  
 *   unsigned char anotherGap[nNoMansLandSize];  
 */  
```  
  
 Die `NoMansLand` Puffer auf beiden Seiten der Datenbereich des Blocks Benutzer sind derzeit 4 Byte lang und mit einem definierten Bytewert, der durch die debugheaproutinen verwendet, um sicherzustellen, dass die Grenzwerte des Speicherblocks des Benutzers nicht überschrieben wurden aufgefüllt werden. Der Debugheap schreibt zusätzlich einen definierten Wert in neue Speicherblöcke. Wenn Sie freigegebene Blöcke, wie nachstehend beschrieben, in der verknüpften Heapliste belassen möchten, erhalten diese ebenfalls einen definierten Wert. Derzeit werden die folgenden Bytewerte verwendet:  
  
 NoMansLand (0xFD)  
 Die "NoMansLand"-Puffer auf beiden Seiten des von der Anwendung verwendeten Speichers enthalten derzeit den Wert 0xFD.  
  
 Freigegebene Blöcke (0xDD)  
 Die freigegebenen Blöcke, die in der verknüpften Heapliste unbenutzt bleiben, wenn das `_CRTDBG_DELAY_FREE_MEM_DF`-Flag festgelegt ist, enthalten derzeit den Wert 0xDD.  
  
 Neue Objekte (0xCD)  
 Neue Objekte werden bei der Reservierung mit 0xCD beschrieben.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS_BackToTop")  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a>Blocktypen auf dem Debugheap  
 Jeder Speicherblock im Debugheap hat einen von fünf möglichen Reservierungstypen. Die Typen werden abhängig von der jeweiligen Aufgabe, z. B. Erkennung von Speicherverlusten und Erstellung von Zustandsberichten, auf unterschiedliche Weise nachverfolgt und ausgegeben. Sie können Blocktyp angeben, indem Sie die Zuordnung mit einem direkten Aufruf der Debugheapreservierungsfunktion wie [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Die fünf Typen von Speicherblöcke im Debugheap (festgelegt der **nBlockUse** Mitglied der **_CrtMemBlockHeader** Struktur) lauten wie folgt:  
  
 **_NORMAL_BLOCK**  
 Ein Aufruf von ["malloc"](/cpp/c-runtime-library/reference/malloc) oder [Calloc](/cpp/c-runtime-library/reference/calloc) einen normalen Block erstellt. Wenn Sie beabsichtigen, die ausschließlich normale Blöcke verwenden und keine Clientblöcke benötigen, sollten Sie definieren [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), die alle Heapreservierungsaufrufe ihren Debugäquivalenten in Debugbuilds zugeordnet werden. Auf diese Weise können die Dateinamen und Zeilennummern zu jedem Reservierungsaufruf im entsprechenden Blockheader gespeichert werden.  
  
 `_CRT_BLOCK`  
 Die Speicherblöcke, die intern von zahlreichen Laufzeitbibliotheksfunktionen reserviert werden, sind als CRT-Blöcke gekennzeichnet und können daher gesondert behandelt werden. So haben sie auf die Erkennung von Speicherverlusten und andere Operationen u. U. keinen Einfluss. CRT-Blöcke werden zu keiner Zeit durch eine Reservierungsoperation zugeordnet, erneut reserviert oder freigegeben.  
  
 `_CLIENT_BLOCK`  
 Eine Anwendung kann eine bestimmte Reservierungsgruppe zu Debugzwecken auf besondere Weise nachverfolgen, indem sie diese unter Verwendung expliziter Debugheap-Funktionsaufrufe als Speicherblöcke eines bestimmten Typs reserviert. Beispielsweise reserviert MFC alle **CObjects** als Clientblöcke, möglicherweise andere Anwendungen andere Speicherobjekte in Clientblöcken beibehalten. Um die Nachverfolgung feiner abzustufen, können auch Untertypen von Clientblöcken definiert werden. Untertypen von Clientblöcken werden festgelegt, indem Sie die Zahl um 16 Bits nach links verschieben und eine `OR`-Operation mit `_CLIENT_BLOCK` ausführen. Zum Beispiel:  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 Eine Client bereitgestellte Hookfunktion zum Ausgeben der in Clientblöcken gespeicherten Objekte kann installiert werden, mithilfe von [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), und wird dann aufgerufen, wenn ein Clientblock durch eine Debugfunktion als Dump ausgegeben wird. Darüber hinaus [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects) können verwendet werden, um eine bestimmte Funktion von der Anwendung für jeden Clientblock im Debugheap aufzurufen.  
  
 **_FREE_BLOCK**  
 Normalerweise werden freigegebene Blöcke aus der Liste entfernt. Wenn Sie jedoch überprüfen möchten, ob weiterhin in freigegebene Blöcke geschrieben wird, oder wenn Sie Speichermangel simulieren möchten, können Sie die freigegebenen Blöcke auch weiterhin in der verknüpften Liste belassen. Diese Blöcke werden dann als freigegeben gekennzeichnet und mit einem definierten Bytewert (derzeit 0xDD) gefüllt.  
  
 **_IGNORE_BLOCK**  
 Es ist möglich, Debugheapoperationen zeitweilig zu deaktivieren. In diesem Zeitraum werden die Speicherblöcke zwar in der Liste geführt, aber als ignorierte Blöcke gekennzeichnet.  
  
 Um den Typ und Untertyp eines bestimmten Blocks zu bestimmen, verwenden Sie die Funktion [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) sowie die Makros **_BLOCK_TYPE** und **_BLOCK_SUBTYPE**. Die Makros sind wie folgt (in crtdbg.h) definiert:  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a>Überprüfen Sie auf Heapintegrität und Speicherverluste  
 Auf viele Funktionen des Debugheaps muss über den Code zugegriffen werden. Im folgenden Abschnitt werden einige Funktionen und ihre Verwendung beschrieben.  
  
 `_CrtCheckMemory`  
 Sie können einen Aufruf von [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory), z. B. die Heapintegrität jederzeit zu überprüfen. Diese Funktion liest jeden Speicherblock im Heap, überprüft die Headerinformationen im Speicherblock auf ihre Gültigkeit und bestätigt, dass die Puffer nicht geändert wurden.  
  
 `_CrtSetDbgFlag`  
 Sie können steuern, wie der Debugheap ein internes Flag, mit der nachverfolgt [_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag), gelesen und festgelegt werden können die [_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag) Funktion. Indem Sie dieses Flag ändern, können Sie den Debugheap anweisen, beim Beenden des Programms mögliche Speicherverluste zu ermitteln und ggf. einen Speicherverlustbericht auszugeben. Entsprechend können Sie festlegen, dass freigegebene Speicherblöcke nicht aus der verknüpften Liste entfernt werden, um beispielsweise Speichermangel zu simulieren. Beim Überprüfen des Heaps werden die freigegebenen Blöcke insgesamt kontrolliert, um sicherzustellen, dass sie nicht behindert wurden.  
  
 Die **_crtDbgFlag** Flag enthält die folgenden Bitfelder:  
  
|Bitfeld|Standard<br /><br /> Wert|Beschreibung|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|Ein|Aktiviert die Debugreservierung. Wenn dieses Bit deaktiviert ist, bleiben die miteinander verkettet werden, aber ihr Blocktyp wird **_IGNORE_BLOCK**.|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|Aus|Verhindert die Freigabe von Speicher, um beispielsweise Speichermangel zu simulieren. Wenn dieses Bit aktiviert ist, freigegebene Blöcke in der verknüpften Heapliste beibehalten werden, jedoch werden als **_FREE_BLOCK** und mit einer speziellen Bytewert gefüllt.|  
|**_CRTDBG_CHECK_ALWAYS_DF**|Aus|Bewirkt, dass **_CrtCheckMemory** bei jeder speicherbelegung und Aufhebung der Zuordnung aufgerufen werden. Dies verlangsamt zwar die Ausführung, beschleunigt aber die Fehlersuche.|  
|**_CRTDBG_CHECK_CRT_DF**|Aus|Bewirkt, dass Blöcke vom Typ **_CRT_BLOCK** , bei der Erkennung von Speicherverlusten und Status Unterschied eingeschlossen werden sollen. Wenn dieses Bit deaktiviert ist, wird der von der Laufzeitbibliothek intern verwendete Speicher während solcher Operationen ignoriert.|  
|**_CRTDBG_LEAK_CHECK_DF**|Aus|Bewirkt, dass Speicherverlust überprüft wird, beim Beenden des Programms über einen Aufruf an erfolgen **_CrtDumpMemoryLeaks**. Wenn die Anwendung nicht den gesamten belegten Speicher freigeben konnte, wird ein Fehlerbericht generiert.|  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a>Konfigurieren des Debugheap  
 Alle Aufrufe an Heapfunktionen, wie z. B. `malloc`, `free`, `calloc`, `realloc`, `new` und `delete`, werden in die Debugversionen der Funktionen aufgelöst, die auf dem Debugheap arbeiten. Wenn Sie einen Speicherblock freigeben, überprüft der Debugheap automatisch die Pufferintegrität auf beiden Seiten des reservierten Bereichs und erstellt einen Fehlerbericht, falls über den Puffer hinaus geschrieben wurde.  
  
 **Verwenden Sie den Debugheap**  
  
-   Verknüpfen Sie das Debugbuild der Anwendung mit einer Debugversion der C-Laufzeitbibliothek.  
  
 **Ändern eine oder mehrere _crtDbgFlag-Bitfelder und erstellen einen neuen Zustand für das flag**  
  
1.  Rufen Sie `_CrtSetDbgFlag` auf, wobei der `newFlag`-Parameter auf `_CRTDBG_REPORT_FLAG` festgelegt ist (um den aktuellen `_crtDbgFlag`-Zustand zu erhalten), und speichern Sie den Rückgabewert in einer temporären Variablen.  
  
2.  Aktivieren Sie Bits durch `OR`--Verknüpfung (bitweises &#124; Symbol) der temporären Variable mit den entsprechenden Bitmasken (im Anwendungscode durch Manifestkonstanten dargestellt).  
  
3.  Deaktivieren Sie die anderen Bits durch eine `AND`-Verknüpfung (bitweises &-Symbol) der Variablen mit der `NOT`-Negation (bitweises ~-Symbol) der entsprechenden Bitmasks.  
  
4.  Rufen Sie `_CrtSetDbgFlag` auf, wobei der `newFlag`-Parameter auf den in der temporären Variablen gespeicherten Wert festgelegt ist, um den neuen Zustand von `_crtDbgFlag` festzulegen.  
  
 Beispielsweise wird durch die folgenden Codezeilen die automatische Überprüfung auf Speicherverluste aktiviert und die Überprüfung von `_CRT_BLOCK`-Blöcken deaktiviert:  
  
```  
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a>neue Debugheap löschen und _CLIENT_BLOCKs im C++  
 Die Debugversionen der C-Laufzeitbibliothek enthalten Debugversionen der `new`- und `delete`-C++-Operatoren. Bei Verwendung des `_CLIENT_BLOCK`-Zuweisungstyps müssen Sie die Debugversion des `new`-Operators direkt aufrufen oder Makros erstellen, die den `new`-Operator im Debugmodus ersetzen, wie im folgenden Beispiel dargestellt:  
  
```  
/* MyDbgNew.h  
 Defines global operator new to allocate from  
 client blocks  
*/  
  
#ifdef _DEBUG  
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)  
#else  
   #define DEBUG_CLIENTBLOCK  
#endif // _DEBUG  
  
/* MyApp.cpp  
        Use a default workspace for a Console Application to  
 *      build a Debug version of this code  
*/  
  
#include "crtdbg.h"  
#include "mydbgnew.h"  
  
#ifdef _DEBUG  
#define new DEBUG_CLIENTBLOCK  
#endif  
  
int main( )   {  
    char *p1;  
    p1 =  new char[40];  
    _CrtMemDumpAllObjectsSince( NULL );  
}  
```  
  
 Die Debugversion des Operators `delete` funktioniert mit allen Blocktypen und macht daher bei der Kompilierung einer Releaseversion keine Programmänderungen erforderlich.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a>Für den Heapzustand  
 **_CrtMemState**  
  
 Um zu einem bestimmten Zeitpunkt eine zusammenfassende Momentaufnahme des Heapzustands aufzuzeichnen, verwenden Sie die in CRTDBG.H definierte _CrtMemState-Struktur:  
  
```  
typedef struct _CrtMemState  
{  
    // Pointer to the most recently allocated block:  
    struct _CrtMemBlockHeader * pBlockHeader;  
    // A counter for each of the 5 types of block:  
    size_t lCounts[_MAX_BLOCKS];  
    // Total bytes allocated in each block type:  
    size_t lSizes[_MAX_BLOCKS];  
    // The most bytes allocated at a time up to now:  
    size_t lHighWaterCount;  
    // The total bytes allocated at present:  
    size_t lTotalCount;  
} _CrtMemState;  
```  
  
 Diese Struktur speichert einen Zeiger auf den ersten (zuletzt reservierten) Block in der verknüpften Heapliste. Anschließend zeichnet sie in zwei Arrays auf, wie viele Speicherblöcke jedes Typs (_NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK usw.) sich in der Liste befinden und wie viele Bytes für jeden Blocktyp reserviert wurden. Schließlich zeichnet die Struktur auf, wie viele Bytes bisher maximal gleichzeitig im Heap reserviert waren und wie viele Bytes momentan reserviert sind.  
  
 **Andere CRT‑Berichtsfunktionen**  
  
 Die folgenden Funktionen geben den Heapzustand und -inhalt wieder. Diese Informationen werden verwendet, um Speicherverluste und andere Probleme zu erkennen.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Speichert eine Momentaufnahme des Heaps in einer **_CrtMemState** Struktur, die von der Anwendung bereitgestellt.|  
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|Vergleicht zwei Speicherzustandsstrukturen, speichert die Unterschiede in einer dritten Zustandsstruktur und gibt TRUE zurück, falls unterschiedliche Zustände festgestellt wurden.|  
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Gibt einen bestimmten **_CrtMemState** Struktur. Die Struktur kann eine Zustandsmomentaufnahme des Debugheaps oder die Unterschiede zwischen zwei Momentaufnahmen enthalten.|  
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Gibt Informationen zu allen Objekten aus, die seit einer bestimmten Heapmomentaufnahme oder seit Beginn der Ausführung reserviert wurden. Jedes Mal, wenn sie einen Dump erstellt eine **_CLIENT_BLOCK** blockieren, wird eine von der Anwendung bereitgestellte Hookfunktion aufgerufen, falls es sich bei einer mit installiert worden **_CrtSetDumpClient**.|  
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Stellt fest, ob seit dem Programmstart Speicherverluste aufgetreten sind, und gibt ggf. alle reservierten Objekte aus. Jedes Mal, wenn **_CrtDumpMemoryLeaks** sichert eine **_CLIENT_BLOCK** blockieren, wird eine von der Anwendung bereitgestellte Hookfunktion aufgerufen, falls es sich bei einer mit installiert worden **_CrtSetDumpClient**.|  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a>Nachverfolgen von Heapreservierungsanforderungen  
 Die Angabe des Quelldateinamens und der Zeilennummer, in der eine Assertion oder ein Berichtsmakro ausgeführt wird, ist häufig sehr nützlich, um die Fehlerursache festzustellen. Auf Heapreservierungsfunktionen trifft dies in der Regel jedoch nicht zu. Makros können an vielen geeigneten Stellen in der logischen Struktur einer Anwendung eingefügt werden, während eine Reservierung meist in einer speziellen Routine verborgen wird, die zu unterschiedlichen Zeitpunkten von vielen verschiedenen Stellen aus aufgerufen wird. Die Frage ist in der Regel nicht, welche Codezeile eine Fehlreservierung verursacht, sondern welche der vielen tausend Reservierungen durch diese Codezeile fehlerhaft waren und warum.  
  
 **Eindeutige Reservierungsanforderungsnummern und "_crtBreakAlloc"**  
  
 Der gesuchte falsche Heapreservierungsaufruf lässt sich am besten feststellen, wenn man die eindeutige Reservierungsanforderungsnummer jedes Blocks im Debugheap berücksichtigt. Wenn Blockinformationen über eine der Dumpfunktionen ausgegeben werden, wird die Reservierungsanforderungsnummer in geschweiften Klammern angezeigt (z. B. "{36}").  
  
 Sobald Sie die Reservierungsanforderungsnummer eines falsch reservierten Blocks kennen, können übergeben Sie das-Zahl in [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) um einen Haltepunkt zu erstellen. Die Ausführung wird dann unmittelbar vor der Reservierung des betreffenden Blocks unterbrochen, und Sie können zurückverfolgen, welche Routine für den falschen Aufruf verantwortlich ist. Um die erneute Kompilierung zu vermeiden, Sie können die gleiche Aufgabe im Debugger durch Festlegen von **_crtBreakAlloc** auf die Reservierungsanforderungsnummer, die Sie von Interesse sind.  
  
 **Erstellen von Debugversionen von Reservierungsroutinen**  
  
 Etwas komplizierter ist, erstellen Sie Debugversionen eigener Reservierungsroutinen vergleichbar sein, um die **_dbg** -Versionen der [heap Zuordnungsfunktionen](../debugger/debug-versions-of-heap-allocation-functions.md). Sie können dann den Quelldateinamen und die Zeilennummer als Argumente an die zugrunde liegenden Heapreservierungsroutinen übergeben und sofort den Ursprung einer Fehlreservierung feststellen.  
  
 Angenommen, die Anwendung enthält eine häufig verwendete Routine, die etwa wie folgt aussieht:  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 In einer Headerdatei können Sie dann beispielsweise folgenden Code hinzufügen:  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 Als nächstes ändern Sie die Reservierung in der Routine zum Erstellen von Datensätzen wie folgt:  
  
```  
int addNewRecord(struct RecStruct *prevRecord,  
                int recType, int recAccess  
#ifdef _DEBUG  
               , const char *srcFile, int srcLine  
#endif  
    )  
{  
    /* ... code omitted through actual allocation ... */  
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,  
            srcFile, scrLine)) == NULL)  
    /* ... rest of routine omitted too ... */  
}  
```  
  
 Nun werden der Quelldateiname und die Zeilennummer, in der `addNewRecord` aufgerufen wurde, in jedem dadurch reservierten Block im Debugheap gespeichert und beim Überprüfen des Blocks ausgegeben.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)
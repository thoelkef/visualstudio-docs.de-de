---
title: "Details zum CRT-Debugheap | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_BLOCK_SUBTYPE-Makro"
  - "_BLOCK_TYPE-Makro"
  - "_CLIENT_BLOCK-Makro"
  - "_CRT_BLOCK-Makro"
  - "_crtBreakAlloc (globale Variable)"
  - "_CrtCheckMemory-Funktion"
  - "_CRTDBG_ALLOC_MEM_DF-Makro"
  - "_CRTDBG_CHECK_ALWAYS_DF-Makro"
  - "_CRTDBG_CHECK_CRT_DF-Makro"
  - "_CRTDBG_DELAY_FREE_MEM_DF-Makro"
  - "_CRTDBG_LEAK_CHECK_DF-Makro"
  - "_crtDbgFlag-Funktion"
  - "_CrtDoForAllClientObjects-Funktion"
  - "_CrtDumpMemoryLeaks-Funktion"
  - "_CrtMemBlockHeader-Funktion"
  - "_CrtMemCheckpoint-Funktion"
  - "_CrtMemDifference-Funktion"
  - "_CrtMemDumpAllObjectsSince-Funktion"
  - "_CrtMemDumpStatistics-Funktion"
  - "_CrtMemState-Funktion"
  - "_CrtReportBlockType-Funktion"
  - "_CrtSetBreakAlloc-Funktion"
  - "_CrtSetDbgFlag-Funktion"
  - "_CrtSetDumpClient-Funktion"
  - "_FREE_BLOCK-Block"
  - "_IGNORE_BLOCK-Block"
  - "_NORMAL_BLOCK-Block"
  - "Reservierungsanforderungsnummern"
  - "Blöcke, Typen auf dem Debugheap"
  - "Clientblöcke, Angeben von Untertypen"
  - "crtBreakAlloc (globale Variable)"
  - "DBGINT.H (Datei)"
  - "Debugbuilds, Verknüpfen zum Debuggen eines Heaps"
  - "Debugheap"
  - "Debugheap, Aufrufen"
  - "Debugheap, CRT"
  - "Debugheap, Speicherblöcke"
  - "Debugheap, Berichtsfunktionen"
  - "Debugheap, Lösen von Speicherreservierungsproblemen"
  - "Debugheap, Rückverfolgen von Heapreservierungsanforderungen"
  - "Debugheap, Verwendung von C++"
  - "Debuggen [C++], CRT-Debugunterstützung"
  - "Debuggen [C++], Debugheap"
  - "Debuggen [CRT], Heapbezogene Probleme"
  - "Debuggen [Visual Studio], Debugheap"
  - "Debuggen von Speicherverlusten"
  - "delete-Operator, Verwenden des Debugheaps in C++"
  - "Heapzuordnung, Debug"
  - "Heapzuordnung, Rückverfolgen von Anforderungen"
  - "Heapfunktionen"
  - "Berichtsfunktionen für den Heapzustand"
  - "Speicherreservierung, Debugheap"
  - "Speicherblöcke, Reservierungstypen im Debugheap"
  - "Speicherblöcke, Frei"
  - "Speicherverluste, CRT-Debugbibliotheksfunktionen"
  - "Speicherverluste, Verfolgen"
  - "Speicher, Debuggen"
  - "nBlockUse-Methode"
  - "new-Operator, Verwenden des Debugheaps in C++"
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Details zum CRT-Debugheap
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Thema umfasst eine detaillierte Erläuterung des CRT‑Debugheaps.  
  
##  <a name="BKMK_Contents"></a> Inhalt  
 [Suchen von Pufferüberläufen mit Debugheap](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Blocktypen auf dem Debugheap](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Überprüfen auf Heapintegrität und Speicherverluste](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Konfigurieren des Debugheap](#BKMK_Configure_the_debug_heap)  
  
 [Neu, Löschen und _CLIENT_BLOCKs im C++-Debugheap](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Berichtsfunktionen für den Heapzustand](#BKMK_Heap_State_Reporting_Functions)  
  
 [Nachverfolgen von Heapzuweisungsanforderungen](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Suchen von Pufferüberläufen mit Debugheap  
 Zwei der geläufigsten und hartnäckigsten Probleme, denen sich Programmierer immer wieder gegenüber sehen, ist das Überschreiben eines reservierten Pufferendes und Speicherverluste \(wobei die Freigabe der nicht mehr benötigten Belegung fehlschlägt\).  Der Debugheap stellt leistungsfähige Tools bereit, die derartige Speicherbelegungsprobleme beheben helfen.  
  
 Durch die Debugversionen der Heapfunktionen wird die Standard\- oder Basisversion aufgerufen, die in Releasebuilds verwendet wird.  Wenn Sie einen Speicherblock anfordern, belegt der Debugheap\-Manager auf dem Basisheap einen Speicherblock, der geringfügig größer als der angeforderte ist, und gibt einen Zeiger auf den jeweiligen Bereich des Blocks zurück.  Angenommen, die Anwendung enthält den `malloc( 10 )`\-Aufruf.  In einem Releasebuild wird von [malloc](/visual-cpp/c-runtime-library/reference/malloc) die Reservierungsroutine für den Basisheap aufgerufen und eine Reservierung von 10 Bytes angefordert.  In einem Debugbuild wird von `malloc` jedoch [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg) aufgerufen. Dieser ruft anschließend die Reservierungsroutine für den Basisheap auf und fordert eine Reservierung von 10 Bytes sowie etwa 36 Bytes an zusätzlichem Arbeitsspeicher an.  Alle resultierenden Speicherblöcke im Debugheap werden über eine einzelne verknüpfte Liste verbunden und sind nach ihrem Reservierungszeitpunkt angeordnet.  
  
 Der durch die Debugheaproutinen belegte Zusatzspeicher wird wie folgt verwendet: für Verwaltungsinformationen, für Zeiger, die die Debugspeicherblöcke verknüpfen, und für kleine Puffer auf beiden Seiten der Daten, um Überschreibungen des reservierten Bereichs abzufangen.  
  
 Derzeit ist die zum Speichern der Debugheap\-Verwaltungsinformationen verwendete Blockheaderstruktur wie folgt in der Headerdatei **DBGINT.H** deklariert:  
  
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
  
 Die  \-Puffer auf beiden Seiten des Benutzerdatenbereichs belegen derzeit je 4 Bytes. Sie enthalten einen definierten Bytewert, mit dessen Hilfe die Debugheaproutinen sicherstellen, dass die Grenzen des belegten Benutzerspeicherblocks nicht überschrieben wurden.  Der Debugheap schreibt zusätzlich einen definierten Wert in neue Speicherblöcke.  Wenn Sie freigegebene Blöcke, wie nachstehend beschrieben, in der verknüpften Heapliste belassen möchten, erhalten diese ebenfalls einen definierten Wert.  Derzeit werden die folgenden Bytewerte verwendet:  
  
 NoMansLand \(0xFD\)  
 Die "NoMansLand"\-Puffer auf beiden Seiten des von der Anwendung verwendeten Speichers enthalten derzeit den Wert 0xFD.  
  
 Freigegebene Blöcke \(0xDD\)  
 Die freigegebenen Blöcke, die in der verknüpften Heapliste unbenutzt bleiben, wenn das `_CRTDBG_DELAY_FREE_MEM_DF`\-Flag festgelegt ist, enthalten derzeit den Wert 0xDD.  
  
 Neue Objekte \(0xCD\)  
 Neue Objekte werden bei der Reservierung mit 0xCD beschrieben.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Blocktypen auf dem Debugheap  
 Jeder Speicherblock im Debugheap hat einen von fünf möglichen Reservierungstypen.  Die Typen werden abhängig von der jeweiligen Aufgabe, z. B. Erkennung von Speicherverlusten und Erstellung von Zustandsberichten, auf unterschiedliche Weise nachverfolgt und ausgegeben.  Sie legen den Blocktyp fest, indem Sie ihn durch den direkten Aufruf der Debugheapreservierungsfunktion, z. B. [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg), reservieren.  Es gibt die folgenden fünf Speicherblocktypen im Debugheap \(sie werden im **nBlockUse**\-Member der **\_CrtMemBlockHeader**\-Struktur festgelegt\):  
  
 **\_NORMAL\_BLOCK**  
 Durch einen Aufruf von [malloc](/visual-cpp/c-runtime-library/reference/malloc) oder [calloc](/visual-cpp/c-runtime-library/reference/calloc) wird ein normaler Block erstellt.  Wenn Sie ausschließlich normale Blöcke verwenden möchten und keine Clientblöcke benötigen, können Sie [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) definieren, wodurch alle Heapreservierungsaufrufe ihren Debugäquivalenten in Debugbuilds zugeordnet werden.  Auf diese Weise können die Dateinamen und Zeilennummern zu jedem Reservierungsaufruf im entsprechenden Blockheader gespeichert werden.  
  
 `_CRT_BLOCK`  
 Die Speicherblöcke, die intern von zahlreichen Laufzeitbibliotheksfunktionen reserviert werden, sind als CRT\-Blöcke gekennzeichnet und können daher gesondert behandelt werden.  So haben sie auf die Erkennung von Speicherverlusten und andere Operationen u. U. keinen Einfluss.  CRT\-Blöcke werden zu keiner Zeit durch eine Reservierungsoperation zugeordnet, erneut reserviert oder freigegeben.  
  
 `_CLIENT_BLOCK`  
 Eine Anwendung kann eine bestimmte Reservierungsgruppe zu Debugzwecken auf besondere Weise nachverfolgen, indem sie diese unter Verwendung expliziter Debugheap\-Funktionsaufrufe als Speicherblöcke eines bestimmten Typs reserviert.  Beispielsweise reserviert MFC alle **CObjects** als Clientblöcke, während andere Anwendungen andere Speicherobjekte in Clientblöcken verwalten können.  Um die Nachverfolgung feiner abzustufen, können auch Untertypen von Clientblöcken definiert werden.  Untertypen von Clientblöcken werden festgelegt, indem Sie die Zahl um 16 Bits nach links verschieben und eine `OR`\-Operation mit `_CLIENT_BLOCK` ausführen.  Beispiel:  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 Eine vom Client bereitgestellte Hookfunktion zum Ausgeben der in Clientblöcken gespeicherten Objekte kann mithilfe von [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient) installiert werden. Sie wird immer dann aufgerufen, wenn ein Clientblock durch eine Debugfunktion als Dump ausgegeben wird.  Auch [\_CrtDoForAllClientObjects](/visual-cpp/c-runtime-library/reference/crtdoforallclientobjects) kann dazu verwendet werden, eine bestimmte Funktion der Anwendung für jeden Clientblock im Debugheap aufzurufen.  
  
 **\_FREE\_BLOCK**  
 Normalerweise werden freigegebene Blöcke aus der Liste entfernt.  Wenn Sie jedoch überprüfen möchten, ob weiterhin in freigegebene Blöcke geschrieben wird, oder wenn Sie Speichermangel simulieren möchten, können Sie die freigegebenen Blöcke auch weiterhin in der verknüpften Liste belassen. Diese Blöcke werden dann als freigegeben gekennzeichnet und mit einem definierten Bytewert \(derzeit 0xDD\) gefüllt.  
  
 **\_IGNORE\_BLOCK**  
 Es ist möglich, Debugheapoperationen zeitweilig zu deaktivieren.  In diesem Zeitraum werden die Speicherblöcke zwar in der Liste geführt, aber als ignorierte Blöcke gekennzeichnet.  
  
 Um den Typ und Untertyp eines bestimmten Blocks zu bestimmen, verwenden Sie die [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype)\-Funktion sowie die Makros **\_BLOCK\_TYPE** und **\_BLOCK\_SUBTYPE**.  Die Makros sind wie folgt \(in **crtdbg.h**\) definiert:  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Überprüfen auf Heapintegrität und Speicherverluste  
 Auf viele Features des Debugheaps muss über den Code zugegriffen werden.  Im folgenden Abschnitt werden einige Features und ihre Verwendung beschrieben.  
  
 `_CrtCheckMemory`  
 Die Heapintegrität kann beispielsweise jederzeit mit einem Aufruf von [\_CrtCheckMemory](/visual-cpp/c-runtime-library/reference/crtcheckmemory) überprüft werden.  Diese Funktion liest jeden Speicherblock im Heap, überprüft die Headerinformationen im Speicherblock auf ihre Gültigkeit und bestätigt, dass die Puffer nicht geändert wurden.  
  
 `_CrtSetDbgFlag`  
 Mit dem internen [\_crtDbgFlag](/visual-cpp/c-runtime-library/crtdbgflag)\-Flag kann gesteuert werden, wie Reservierungen vom Debugheap nachverfolgt werden. Das Flag kann mit der [\_CrtSetDbgFlag](/visual-cpp/c-runtime-library/reference/crtsetdbgflag)\-Funktion gelesen und festgelegt werden.  Indem Sie dieses Flag ändern, können Sie den Debugheap anweisen, beim Beenden des Programms mögliche Speicherverluste zu ermitteln und ggf. einen Speicherverlustbericht auszugeben.  Entsprechend können Sie festlegen, dass freigegebene Speicherblöcke nicht aus der verknüpften Liste entfernt werden, um beispielsweise Speichermangel zu simulieren.  Beim Überprüfen des Heaps werden die freigegebenen Blöcke insgesamt kontrolliert, um sicherzustellen, dass sie nicht behindert wurden.  
  
 Das **\_crtDbgFlag**\-Flag enthält die folgenden Bitfelder:  
  
|Bitfeld|Default<br /><br /> Wert|Beschreibung|  
|-------------|----------------------|------------------|  
|**\_CRTDBG\_ALLOC\_MEM\_DF**|On|Aktiviert die Debugreservierung.  Wenn dieses Bit deaktiviert ist, bleiben die reservierten Blöcke weiterhin verknüpft, ihr Blocktyp wird jedoch zu **\_IGNORE\_BLOCK**.|  
|**\_CRTDBG\_DELAY\_FREE\_MEM\_DF**|Off|Verhindert die Freigabe von Speicher, um beispielsweise Speichermangel zu simulieren.  Wenn dieses Bit aktiviert ist, werden die freigegebenen Blöcke weiterhin in der verknüpften Liste verwaltet, jedoch als **\_FREE\_BLOCK** gekennzeichnet und mit einem definierten Bytewert gefüllt.|  
|**\_CRTDBG\_CHECK\_ALWAYS\_DF**|Off|Bewirkt den Aufruf von **\_CrtCheckMemory** bei jeder Speicherbelegung und jedem Aufheben der Speicherbelegung.  Dies verlangsamt zwar die Ausführung, beschleunigt aber die Fehlersuche.|  
|**\_CRTDBG\_CHECK\_CRT\_DF**|Off|Bewirkt, dass Blöcke vom Typ **\_CRT\_BLOCK** in Operationen, die Speicherverluste und unterschiedliche Zustände feststellen sollen, eingeschlossen werden.  Wenn dieses Bit deaktiviert ist, wird der von der Laufzeitbibliothek intern verwendete Speicher während solcher Operationen ignoriert.|  
|**\_CRTDBG\_LEAK\_CHECK\_DF**|Off|Bewirkt, dass Überprüfungen auf Speicherverluste beim Beenden des Programms durch einen **\_CrtDumpMemoryLeaks**\-Aufruf durchgeführt werden.  Wenn die Anwendung nicht den gesamten belegten Speicher freigeben konnte, wird ein Fehlerbericht generiert.|  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> Konfigurieren des Debugheap  
 Alle Aufrufe an Heapfunktionen, wie z. B. `malloc`, `free`, `calloc`, `realloc`, `new` und `delete`, werden in die Debugversionen der Funktionen aufgelöst, die auf dem Debugheap arbeiten.  Wenn Sie einen Speicherblock freigeben, überprüft der Debugheap automatisch die Pufferintegrität auf beiden Seiten des reservierten Bereichs und erstellt einen Fehlerbericht, falls über den Puffer hinaus geschrieben wurde.  
  
 **So verwenden Sie den Debugheap**  
  
-   Verknüpfen Sie das Debugbuild der Anwendung mit einer Debugversion der C\-Laufzeitbibliothek.  
  
 **So ändern Sie eines oder mehrere \_crtDbgFlag\-Bitfelder sowie den Flagzustand**  
  
1.  Rufen Sie `_CrtSetDbgFlag` auf, wobei der `newFlag`\-Parameter auf `_CRTDBG_REPORT_FLAG` festgelegt ist \(um den aktuellen `_crtDbgFlag`\-Zustand zu erhalten\), und speichern Sie den Rückgabewert in einer temporären Variablen.  
  
2.  Aktivieren Sie die Bits durch eine `OR`\-Verknüpfung \(bitweises &#124;\-Symbol\) der temporären Variable mit den entsprechenden Bitmasken \(im Anwendungscode durch Manifestkonstanten dargestellt\).  
  
3.  Deaktivieren Sie die anderen Bits durch eine `AND`\-Verknüpfung \(bitweises &\-Symbol\) der Variablen mit der `NOT`\-Negation \(bitweises ~\-Symbol\) der entsprechenden Bitmasks.  
  
4.  Rufen Sie `_CrtSetDbgFlag` auf, wobei der `newFlag`\-Parameter auf den in der temporären Variablen gespeicherten Wert festgelegt ist, um den neuen Zustand von `_crtDbgFlag` festzulegen.  
  
 Beispielsweise wird durch die folgenden Codezeilen die automatische Überprüfung auf Speicherverluste aktiviert und die Überprüfung von `_CRT_BLOCK`\-Blöcken deaktiviert:  
  
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
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> Neu, Löschen und \_CLIENT\_BLOCKs im C\+\+\-Debugheap  
 Die Debugversionen der C\-Laufzeitbibliothek enthalten Debugversionen der `new`\- und `delete`\-C\+\+\-Operatoren.  Bei Verwendung des `_CLIENT_BLOCK`\-Zuweisungstyps müssen Sie die Debugversion des `new`\-Operators direkt aufrufen oder Makros erstellen, die den `new`\-Operator im Debugmodus ersetzen, wie im folgenden Beispiel dargestellt:  
  
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
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> Berichtsfunktionen für den Heapzustand  
 **"\_CrtMemState"**  
  
 Um zu einem bestimmten Zeitpunkt eine zusammenfassende Momentaufnahme des Heapzustands aufzuzeichnen, verwenden Sie die in CRTDBG.H definierte \_CrtMemState\-Struktur:  
  
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
  
 Diese Struktur speichert einen Zeiger auf den ersten \(zuletzt reservierten\) Block in der verknüpften Heapliste.  Anschließend zeichnet sie in zwei Arrays auf, wie viele Speicherblöcke jedes Typs \(\_NORMAL\_BLOCK, `_CLIENT_BLOCK`, \_FREE\_BLOCK usw.\) sich in der Liste befinden und wie viele Bytes für jeden Blocktyp reserviert wurden.  Schließlich zeichnet die Struktur auf, wie viele Bytes bisher maximal gleichzeitig im Heap reserviert waren und wie viele Bytes momentan reserviert sind.  
  
 **Andere CRT‑Berichtsfunktionen**  
  
 Die folgenden Funktionen geben den Heapzustand und \-inhalt wieder. Diese Informationen werden verwendet, um Speicherverluste und andere Probleme zu erkennen.  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|[\_CrtMemCheckpoint](/visual-cpp/c-runtime-library/reference/crtmemcheckpoint)|Speichert eine Heapmomentaufnahme in einer von der Anwendung bereitgestellten **\_CrtMemState**\-Struktur.|  
|[\_CrtMemDifference](/visual-cpp/c-runtime-library/reference/crtmemdifference)|Vergleicht zwei Speicherzustandsstrukturen, speichert die Unterschiede in einer dritten Zustandsstruktur und gibt TRUE zurück, falls unterschiedliche Zustände festgestellt wurden.|  
|[\_CrtMemDumpStatistics](/visual-cpp/c-runtime-library/reference/crtmemdumpstatistics)|Gibt eine bestimmte **\_CrtMemState**\-Struktur aus.  Die Struktur kann eine Zustandsmomentaufnahme des Debugheaps oder die Unterschiede zwischen zwei Momentaufnahmen enthalten.|  
|[\_CrtMemDumpAllObjectsSince](/visual-cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Gibt Informationen zu allen Objekten aus, die seit einer bestimmten Heapmomentaufnahme oder seit Beginn der Ausführung reserviert wurden.  Bei jedem Dump eines **\_CLIENT\_BLOCK**\-Blocks wird eine von der Anwendung bereitgestellte Hookfunktion aufgerufen, falls eine solche mit **\_CrtSetDumpClient** installiert wurde.|  
|[\_CrtDumpMemoryLeaks](/visual-cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Stellt fest, ob seit dem Programmstart Speicherverluste aufgetreten sind, und gibt ggf. alle reservierten Objekte aus.  Wenn **\_CrtDumpMemoryLeaks** einen **\_CLIENT\_BLOCK**\-Block ausgibt, wird eine von der Anwendung bereitgestellte Hookfunktion aufgerufen, falls eine solche mit **\_CrtSetDumpClient** installiert wurde.|  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> Nachverfolgen von Heapzuweisungsanforderungen  
 Die Angabe des Quelldateinamens und der Zeilennummer, in der eine Assertion oder ein Berichtsmakro ausgeführt wird, ist häufig sehr nützlich, um die Fehlerursache festzustellen. Auf Heapreservierungsfunktionen trifft dies in der Regel jedoch nicht zu.  Makros können an vielen geeigneten Stellen in der logischen Struktur einer Anwendung eingefügt werden, während eine Reservierung meist in einer speziellen Routine verborgen wird, die zu unterschiedlichen Zeitpunkten von vielen verschiedenen Stellen aus aufgerufen wird.  Die Frage ist in der Regel nicht, welche Codezeile eine Fehlreservierung verursacht, sondern welche der vielen tausend Reservierungen durch diese Codezeile fehlerhaft waren und warum.  
  
 **Eindeutige Reservierungsanforderungsnummern und "\_crtBreakAlloc"**  
  
 Der gesuchte falsche Heapreservierungsaufruf lässt sich am besten feststellen, wenn man die eindeutige Reservierungsanforderungsnummer jedes Blocks im Debugheap berücksichtigt.  Wenn Blockinformationen über eine der Dumpfunktionen ausgegeben werden, wird die Reservierungsanforderungsnummer in geschweiften Klammern angezeigt \(z. B. "{36}"\).  
  
 Wenn Sie die Reservierungsanforderungsnummer eines falsch reservierten Blocks kennen, können Sie diese Nummer an [\_CrtSetBreakAlloc](/visual-cpp/c-runtime-library/reference/crtsetbreakalloc) übergeben, um einen Haltepunkt zu erstellen.  Die Ausführung wird dann unmittelbar vor der Reservierung des betreffenden Blocks unterbrochen, und Sie können zurückverfolgen, welche Routine für den falschen Aufruf verantwortlich ist.  Um eine erneute Kompilierung zu vermeiden, können Sie im Debugger genauso verfahren, indem Sie **\_crtBreakAlloc** auf die gewünschte Reservierungsanforderungsnummer festlegen.  
  
 **Erstellen von Debugversionen von Reservierungsroutinen**  
  
 Etwas komplizierter ist ein anderes Verfahren, bei dem Sie Debugversionen eigener Reservierungsroutinen erstellen. Diese sind vergleichbar mit den **\_dbg**\-Versionen der [Heapreservierungsfunktionen](../debugger/debug-versions-of-heap-allocation-functions.md).  Sie können dann den Quelldateinamen und die Zeilennummer als Argumente an die zugrunde liegenden Heapreservierungsroutinen übergeben und sofort den Ursprung einer Fehlreservierung feststellen.  
  
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
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
## Siehe auch  
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)
---
title: MFC Debugtechniken | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c795e978de3911b3c5e815583c32e878fd7b173
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696902"
---
# <a name="mfc-debugging-techniques"></a>MFC-Debugverfahren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die folgenden Debugverfahren können beim Debuggen von MFC‑Programmen hilfreich sein:  
  
## <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [AfxDebugBreak](#BKMK_AfxDebugBreak)  
  
 [Das TRACE-Makro](#BKMK_The_TRACE_macro)  
  
 [Feststellen von Speicherverlusten in MFC](#BKMK_Memory_leak_detection_in_MFC)  
  
- [Nachverfolgen der Speicherbelegung](#BKMK_Tracking_memory_allocations)  
  
- [Aktivieren der Speicherdiagnose](#BKMK_Enabling_memory_diagnostics)  
  
- [Aufzeichnen von Speichermomentaufnahmen](#BKMK_Taking_memory_snapshots)  
  
- [Anzeigen einer Speicherstatistik](#BKMK_Viewing_memory_statistics)  
  
- [Nachverfolgen von Objektabbildern](#BKMK_Taking_object_dumps)  
  
  - [Interpretieren von Speicherabbildern](#BKMK_Interpreting_memory_dumps)  
  
  - [Anpassen von Objektdumps](#BKMK_Customizing_object_dumps)  
  
    [Verringern der Größe eines MFC-Debugbuilds](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)  
  
  - [So erstellen Sie eine MFC‑Anwendung mit Debuginformationen für ausgewählte Module](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)  
  
## <a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak  
 MFC bietet eine spezielle [AfxDebugBreak](https://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) -Funktion für hart codierte Haltepunkte im Quellcode:  
  
```  
AfxDebugBreak( );  
  
```  
  
 Auf Intel-Plattformen generiert `AfxDebugBreak` den folgenden Code, der zu Unterbrechungen im Quellcode und nicht im Kernelcode führt:  
  
```  
_asm int 3  
```  
  
 Auf anderen Plattformen wird durch `AfxDebugBreak` lediglich `DebugBreak`aufgerufen.  
  
 Achten Sie darauf, die `AfxDebugBreak` -Anweisungen vor dem Erstellen eines Releasebuilds zu entfernen oder sie in `#ifdef _DEBUG` einzuschließen.  
  
 [Inhalt](#BKMK_In_this_topic)  
  
## <a name="BKMK_The_TRACE_macro"></a> Das TRACE-Makro  
 Um Programmmeldungen im [Ausgabefenster](../ide/reference/output-window.md)des Debuggers anzuzeigen, können Sie das [ATLTRACE](https://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e) -Makro oder das MFC- [TRACE](https://msdn.microsoft.com/library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) -Makro verwenden. Wie [Assertions](../debugger/c-cpp-assertions.md)sind auch TRACE-Makros nur in der Debugversion des Programms aktiv und werden bei der Kompilierung der endgültigen Produktversion entfernt.  
  
 Die folgenden Beispiele zeigen einige Verwendungsmöglichkeiten für das **TRACE** -Makro auf. Ähnlich wie `printf`ist das **TRACE** -Makro in der Lage, mehrere Argumente zu verarbeiten.  
  
```  
int x = 1;  
int y = 16;  
float z = 32.0;  
TRACE( "This is a TRACE statement\n" );  
  
TRACE( "The value of x is %d\n", x );  
  
TRACE( "x = %d and y = %d\n", x, y );  
  
TRACE( "x = %d and y = %x and z = %f\n", x, y, z );  
```  
  
 Das TRACE-Makro behandelt char*- und wchar_t\*-Parameter ordnungsgemäß. In den folgenden Beispielen wird die Verwendung des TRACE-Makros mit unterschiedlichen Zeichenfolgenparametertypen veranschaulicht.  
  
```  
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);  
  
TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);  
  
TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);  
  
```  
  
 Weitere Informationen zum **TRACE** -Makro finden Sie unter [Diagnosedienste](https://msdn.microsoft.com/library/8d78454f-9fae-49c2-88c9-d3fabd5393e8).  
  
 [Inhalt](#BKMK_In_this_topic)  
  
## <a name="BKMK_Memory_leak_detection_in_MFC"></a> Feststellen von Speicherverlusten in MFC  
 MFC stellt Klassen und Funktionen bereit, mit deren Hilfe Speicherbereiche ermittelt werden können, die belegt, jedoch nicht wieder freigegeben werden.  
  
### <a name="BKMK_Tracking_memory_allocations"></a> Nachverfolgen der Speicherbelegung  
 In MFC können Sie anstelle des Operators [new](https://msdn.microsoft.com/library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) auch das **DEBUG_NEW** -Makro verwenden, um Speicherverluste aufzudecken. In der Debugversion des Programms werden durch `DEBUG_NEW` die Dateinamen und Zeilennummern jedes von ihm reservierten Objekts nachverfolgt. Wenn Sie eine Releaseversion des Programms kompilieren, wird `DEBUG_NEW` in eine einfache **new** -Operation aufgelöst, ohne dass Dateinamen und Zeilennummern aufgelöst werden. Folglich wird die Ausführungsgeschwindigkeit der Releaseversion des Programms nicht beeinträchtigt.  
  
 Wenn Sie nicht das gesamte Programm umschreiben möchten, um `DEBUG_NEW` anstelle von **new**zu verwenden, können Sie dieses Makro in den Quellcodedateien definieren:  
  
```  
#define new DEBUG_NEW  
```  
  
 Wenn Sie einen [Objektdump](#BKMK_Taking_object_dumps)erstellen, wird für jedes mit `DEBUG_NEW` zugeordnete Objekt der Dateiname und die Zeilennummer der Stelle angezeigt, an der es reserviert wurde. Auf diese Weise lässt sich die Ursache für Speicherverluste eindeutig ermitteln.  
  
 In der Debugversion des MFC-Frameworks wird `DEBUG_NEW` automatisch verwendet, im Code jedoch nicht. Um die Vorteile von `DEBUG_NEW`nutzen zu können, müssen Sie `DEBUG_NEW` explizit oder **#define new** , wie oben dargestellt, verwenden.  
  
 [Inhalt](#BKMK_In_this_topic)  
  
### <a name="BKMK_Enabling_memory_diagnostics"></a> Aktivieren der Speicherdiagnose  
 Damit Sie die Speicherdiagnosefeatures nutzen können, muss die Diagnosenachverfolgung aktiviert werden.  
  
 **So aktivieren oder deaktivieren Sie die Speicherdiagnose**  
  
- Rufen Sie die globale [AfxEnableMemoryTracking](https://msdn.microsoft.com/library/0a40e0c4-855d-46e2-9577-a8f2346f47db) -Funktion auf, um die Diagnose-Speicherbelegungsfunktion zu aktivieren oder zu deaktivieren. Da die Speicherdiagnose in der Debugbibliothek standardmäßig aktiviert ist, wird diese Funktion in der Regel verwendet, um die Speicherdiagnose vorübergehend zu deaktivieren. Auf diese Weise wird die Programmausführung beschleunigt und die Diagnoseausgabe reduziert.  
  
  **So wählen Sie spezifische Speicherdiagnosefeatures mit "afxMemDF" aus**  
  
- Wenn Sie die Speicherdiagnosefeatures präziser steuern möchten, können Sie einzelne Features gezielt aktivieren und deaktivieren, indem Sie den Wert der globalen MFC-Variablen [afxMemDF](https://msdn.microsoft.com/library/cf117501-5446-4fce-81b3-f7194bc95086)festlegen. Diese Variable wird über den enumerierten **afxMemDF**-Typ festgelegt und kann folgende Werte annehmen:  
  
  |Wert|Beschreibung|  
  |-----------|-----------------|  
  |**allocMemDF**|Aktivieren der Diagnose-Speicherbelegungsfunktion (Standard).|  
  |**delayFreeMemDF**|Verzögern der Speicherfreigabe nach dem Aufrufen von `delete` oder `free` bis zum Programmende. Auf diese Weise belegt das Programm den größtmöglichen Speicherplatz.|  
  |**checkAlwaysMemDF**|Aufrufen von [AfxCheckMemory](https://msdn.microsoft.com/library/4644da71-7d14-41dc-adc0-ee9558fd7a28) bei jeder Speicherbelegung oder -freigabe.|  
  
   Diese Werte können mit logischen OR-Operationen auch kombiniert werden, z. B.:  
  
  ```cpp  
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;  
  ```  
  
  [Inhalt](#BKMK_In_this_topic)  
  
### <a name="BKMK_Taking_memory_snapshots"></a> Aufzeichnen von Speichermomentaufnahmen  
  
1. Erstellen Sie ein [CMemoryState](https://msdn.microsoft.com/8fade6e9-c6fb-4b2a-8565-184a912d26d2) -Objekt, und rufen Sie die [CMemoryState::Checkpoint](https://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a) -Memberfunktion auf. Dadurch wird die erste Speichermomentaufnahme erstellt.  
  
2. Nachdem das Programm alle Speicherbelegungen und -freigaben vorgenommen hat, erstellen Sie ein weiteres `CMemoryState` -Objekt und rufen `Checkpoint` für dieses Objekt auf. Dadurch wird eine zweite Momentaufnahme erstellt, die Aufschluss über die Arbeitsspeichernutzung gibt.  
  
3. Erstellen Sie ein drittes `CMemoryState` -Objekt, rufen Sie die zugehörige [CMemoryState::Difference](https://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) -Memberfunktion auf, und übergeben Sie die ersten beiden `CMemoryState` -Objekte als Argumente. Wenn sich die beiden Speicherzustände unterscheiden, gibt die `Difference` -Funktion einen Wert ungleich 0 (Null) zurück. Dies deutet darauf hin, dass einige Speicherblöcke nicht freigegeben wurden.  
  
    Dieses Beispiel veranschaulicht den dazugehörigen Code:  
  
   ```  
   // Declare the variables needed  
   #ifdef _DEBUG  
       CMemoryState oldMemState, newMemState, diffMemState;  
       oldMemState.Checkpoint();  
   #endif  
  
       // Do your memory allocations and deallocations.  
       CString s("This is a frame variable");  
       // The next object is a heap object.  
      CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
  
   #ifdef _DEBUG  
       newMemState.Checkpoint();  
       if( diffMemState.Difference( oldMemState, newMemState ) )  
       {  
           TRACE( "Memory leaked!\n" );  
       }  
   #endif  
   ```  
  
    Beachten Sie, dass die Speicherüberprüfungsanweisungen in `#ifdef`[_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a)/ **#endif** -Blöcke eingeschlossen sind und daher nur in Debugversionen des Programms kompiliert werden.  
  
    Da Sie nun wissen, dass ein Speicherverlust auftritt, können Sie eine andere Memberfunktion namens [CMemoryState::DumpStatistics](https://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) verwenden, um die Stelle zu lokalisieren.  
  
   [Inhalt](#BKMK_In_this_topic)  
  
### <a name="BKMK_Viewing_memory_statistics"></a> Anzeigen einer Speicherstatistik  
 Durch die [CMemoryState::Difference](https://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) -Funktion werden die beiden Speicherzustandsobjekte verglichen und alle Objekte ermittelt, die zwischen dem Anfangs- und dem Endzustand nicht vom Heap freigegeben wurden. Nachdem Sie Speichermomentaufnahmen aufgezeichnet und diese mithilfe von `CMemoryState::Difference`verglichen haben, können Sie [CMemoryState::DumpStatistics](https://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) aufrufen, um Informationen über die nicht freigegebenen Objekte zu erhalten.  
  
 Betrachten Sie das folgende Beispiel:  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpStatistics();  
}  
```  
  
 Ein Beispieldump dieses Codes sieht z. B. wie folgt aus:  
  
```  
0 bytes in 0 Free Blocks  
22 bytes in 1 Object Blocks  
45 bytes in 4 Non-Object Blocks  
Largest number used: 67 bytes  
Total allocations: 67 bytes  
```  
  
 Bei freien Blöcken handelt es sich um die Blöcke, deren Freigabe verzögert wird, wenn `afxMemDF` auf `delayFreeMemDF`festgelegt wurde.  
  
 Die in der zweiten Zeile aufgeführten normalen Objektblöcke bleiben auf dem Heap reserviert.  
  
 Nicht-Objektblöcke umfassen Arrays und Strukturen, die mit `new`reserviert wurden. In diesem Fall wurden vier Elemente, die kein Objekt darstellen, auf dem Heap reserviert, jedoch nicht freigegeben.  
  
 `Largest number used` gibt an, wie viel Speicher vom Programm maximal reserviert wurde.  
  
 `Total allocations` gibt die gesamte, vom Programm genutzte Arbeitsspeicherkapazität an.  
  
 [Inhalt](#BKMK_In_this_topic)  
  
### <a name="BKMK_Taking_object_dumps"></a> Nachverfolgen von Objektabbildern  
 Sie können in einem MFC-Programm verwenden [CMemoryState](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) um eine Beschreibung aller Objekte im Heap zu sichern, die nicht freigegeben wurden. `DumpAllObjectsSince` sichert alle seit dem letzten [CMemoryState::Checkpoint](https://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a)aufgerufen. Wurde kein `Checkpoint` -Aufruf durchgeführt, gibt `DumpAllObjectsSince` alle momentan im Arbeitsspeicher enthaltenen Objekte sowie Elemente, die kein Objekt darstellen, aus.  
  
> [!NOTE]
> Bevor MFC-Objektdumps erstellt werden können, muss die [Diagnosenachverfolgung](../debugger/mfc-debugging-techniques.md#BKMK_Enabling_memory_diagnostics)aktiviert werden.  
  
> [!NOTE]
> In MFC wird von allen Objekten, die Speicherverluste verursachen, beim Beenden des Programms automatisch ein Dump erstellt. Daher ist kein Code zum Erstellen von Objektdumps am Programmende erforderlich.  
  
 Durch den folgenden Code werden alle Objekte auf Speicherverluste getestet, indem die beiden Speicherzustände verglichen und bei Auftreten von Verlusten alle Objekte gesichert werden.  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpAllObjectsSince();  
}  
```  
  
 Im Folgenden der Inhalt des Dumps:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Die in geschweiften Klammern gesetzten Zahlen am Zeilenanfang geben die Reihenfolge an, in der die Objekte reserviert wurden. Das zuletzt reservierte Objekt verfügt über die höchste Nummer und befindet sich im Dump an erster Stelle.  
  
 Die maximal verfügbaren Informationen aus einem Objektdump erhalten Sie, indem Sie die Memberfunktion `Dump` für jedes von `CObject`abgeleitete Objekt überschreiben, um den Objektdump anzupassen.  
  
 Sie können einen Haltepunkt für eine bestimmte Speicherbelegung festlegen, indem Sie für die globale `_afxBreakAlloc` -Variable den in geschweiften Klammern angegebenen Wert festlegen. Wenn das Programm erneut ausgeführt wird, unterbricht der Debugger die Ausführung, sobald diese Reservierung erfolgt. Sie können dann die Aufrufliste durchsehen, um festzustellen, wie das Programm zu diesem Punkt gelangt ist.  
  
 Die C-Laufzeitbibliothek verfügt über eine vergleichbare Funktion, [_CrtSetBreakAlloc](https://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1), die Sie für C-Laufzeitbelegungen verwenden können.  
  
 [Inhalt](#BKMK_In_this_topic)  
  
#### <a name="BKMK_Interpreting_memory_dumps"></a> Interpretieren von Speicherabbildern  
 Im Folgenden wird dieser Objektdump ausführlich erläutert:  
  
```  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Das Programm, das diesen Dump generiert hat, verfügte nur über zwei explizite Reservierungen – eine für den Stapel und eine für den Heap:  
  
```  
// Do your memory allocations and deallocations.  
CString s("This is a frame variable");  
// The next object is a heap object.  
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
```  
  
 Der `CPerson` -Konstruktor hat drei Argumente, die Zeiger auf `char`darstellen. Sie werden zur Initialisierung von `CString` -Membervariablen verwendet. Im Speicherdump ist das `CPerson` -Objekt zusammen mit drei Elementen, die keine Objekte darstellen (3, 4 und 5), aufgeführt. Diese enthalten die Zeichen für die `CString` -Membervariablen und werden beim Aufrufen des `CPerson` -Objektdestruktors nicht gelöscht.  
  
 Block 2 ist das `CPerson` -Objekt selbst. `$51A4` stellt die Adresse des Speicherblocks dar. Es folgt der Objektinhalt, der durch `CPerson`::`Dump` ausgegeben wurde, sofern der Aufruf durch [DumpAllObjectsSince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2)erfolgt ist.  
  
 Block Nummer 1 kann der `CString` -Framevariablen zugeordnet werden. Dies lässt sich aus seiner Größe (entspricht der Anzahl der Zeichen in der `CString` -Variablen) und der Sequenznummer schließen. Reservierungen für Framevariablen werden automatisch freigegeben, wenn die Framevariable den Gültigkeitsbereich verlässt.  
  
 **Framevariablen**  
  
 Im Allgemeinen brauchen Sie sich um Heapobjekte, die mit Framevariablen verknüpft sind, nicht zu kümmern, da sie automatisch freigegeben werden, wenn die Framevariable den Gültigkeitsbereich verlässt. Um übersichtliche Dumps für die Speicherdiagnose zu erhalten, sollten Sie die `Checkpoint` -Aufrufe so positionieren, dass sie nicht im Gültigkeitsbereich von Framevariablen liegen. Schließen Sie beispielsweise den oben genannten Reservierungscode in Klammern ein, die den Gültigkeitsbereich darstellen. Siehe folgenden Code:  
  
```  
oldMemState.Checkpoint();  
{  
    // Do your memory allocations and deallocations ...  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
}  
newMemState.Checkpoint();  
```  
  
 Mit diesen Klammern sieht der Speicherdump für dieses Beispiel wie folgt aus:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
```  
  
 **Nicht-Objektreservierungen**  
  
 Beachten Sie, dass einige Belegungen sich auf Objekte (z. B. `CPerson`) und andere auf „Nicht-Objekte“ beziehen. „Nicht-Objekt-Speicherbelegungen“ sind Speicherbelegungen für Objekte, die nicht von `CObject` abgeleitet wurden, oder Speicherbelegungen primitiver C-Typen wie `char`, `int`oder **long**. Wenn die von **CObject-** abgeleitete Klasse zusätzlichen Arbeitsspeicher reserviert, z. B. für interne Puffer, weisen die Objekte sowohl Objekt- als auch Nicht-Objektreservierungen auf.  
  
 **Verhindern von Speicherverlusten**  
  
 Im obigen Code sehen Sie, dass der mit der `CString` -Framevariablen verknüpfte Speicherblock automatisch freigegeben wurde und nicht als Speicherverlust angezeigt wird. Die automatische Freigabe aufgrund von Gültigkeitsbereichsregeln verhindert normalerweise Speicherverluste in Zusammenhang mit Framevariablen.  
  
 Objekte, für die Speicher auf dem Heap reserviert wird, sollten Sie jedoch explizit löschen, um Speicherverluste zu verhindern. Um den letzten Speicherverlust im oben stehenden Beispiel zu bereinigen, können Sie das `CPerson` -Objekt, für das Heapspeicher reserviert wurde, wie folgt löschen:  
  
```  
{  
    // Do your memory allocations and deallocations.  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
    delete p;  
}  
```  
  
 [Inhalt](#BKMK_In_this_topic)  
  
#### <a name="BKMK_Customizing_object_dumps"></a> Anpassen von Objektdumps  
 Wenn Sie eine Klasse von [CObject](https://msdn.microsoft.com/library/95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a)ableiten, können Sie die Memberfunktion `Dump` überschreiben, um bei Verwendung von [DumpAllObjectsSince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) für den Objektdump zusätzliche Informationen im [Ausgabefenster](../ide/reference/output-window.md)anzuzeigen.  
  
 Die `Dump` -Funktion gibt eine Textdarstellung der objektspezifischen Membervariablen in einem Dumpkontext ([CDumpContext](https://msdn.microsoft.com/library/98c52b2d-14b5-48ed-b423-479a4d1c60fa)) aus. Der Dumpkontext ist mit einem E/A-Stream vergleichbar. Mithilfe des Anfügeoperators (**<<**) können Sie Daten an einen `CDumpContext`aufgerufen.  
  
 Wenn Sie die `Dump` -Funktion überschreiben, sollten Sie zunächst die Basisklassenversion von `Dump` aufrufen, um den Inhalt des Basisklassenobjekts auszugeben. Lassen Sie für jede Membervariable der abgeleiteten Klasse eine Textdarstellung und einen Wert ausgeben.  
  
 Die Deklaration der `Dump` -Funktion sieht wie folgt aus:  
  
```  
class CPerson : public CObject  
{  
public:  
#ifdef _DEBUG  
    virtual void Dump( CDumpContext& dc ) const;  
#endif  
  
    CString m_firstName;  
    CString m_lastName;  
    // And so on...  
};  
```  
  
 Da das Ausgeben von Objekten nur beim Debuggen eines Programms sinnvoll ist, wird die Deklaration der `Dump` -Funktion in einen **#ifdef _DEBUG / #endif** -Block eingeschlossen.  
  
 Im folgenden Beispiel ruft die `Dump` -Funktion zuerst die `Dump` -Funktion für ihre Basisklasse auf. Dann wird eine Kurzbeschreibung jeder Membervariablen sowie der zugehörige Wert in den Diagnosestream geschrieben.  
  
```  
#ifdef _DEBUG  
void CPerson::Dump( CDumpContext& dc ) const  
{  
    // Call the base class function first.  
    CObject::Dump( dc );  
  
    // Now do the stuff for our specific class.  
    dc << "last name: " << m_lastName << "\n"  
        << "first name: " << m_firstName << "\n";  
}  
#endif  
```  
  
 Sie müssen ein `CDumpContext` -Argument angeben, um festzulegen, wo der Dump ausgegeben wird. Die Debugversion von MFC bietet ein vordefiniertes `CDumpContext` -Objekt mit dem Namen `afxDump` , durch das die Ausgabe an den Debugger gesendet wird.  
  
```  
CPerson* pMyPerson = new CPerson;  
// Set some fields of the CPerson object.  
//...  
// Now dump the contents.  
#ifdef _DEBUG  
pMyPerson->Dump( afxDump );  
#endif  
```  
  
 [Inhalt](#BKMK_In_this_topic)  
  
## <a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Verringern der Größe eines MFC-Debugbuilds  
 Die Debuginformationen für eine umfangreiche MFC-Anwendung können sehr viel Speicherplatz beanspruchen. Sie können eine dieser Prozeduren zum Verringern der Größe verwenden:  
  
1. Die MFC‑Bibliotheken mithilfe der [/Z7, / Zi, / Zi (Debuginformationsformat)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) -Option anstelle von **"/ Z7"**. Durch diese Optionen wird eine einzelne Programmdatenbank-Datei (PDB) mit Debuginformationen für die gesamte Bibliothek erstellt, wodurch Redundanz und Speicherplatzanforderungen verringert werden.  
  
2. Erstellen Sie die MFC-Bibliotheken ohne Debuginformationen neu (keine [/Z7, / Zi, / Zi (Debuginformationsformat)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) Option). In diesem Fall werden Sie die meisten Debuggerfunktionen aufgrund fehlender Debuginformationen innerhalb des MFC-Bibliothekscodes nicht nutzen können. Da die MFC-Bibliotheken jedoch bereits eingehend gedebuggt wurden, stellt dies u. U. kein Problem dar.  
  
3. Erstellen Sie eine eigene Anwendung mit modulspezifischen Debuginformationen nur wie unten beschrieben.  
  
   [In diesem Thema](#BKMK_In_this_topic)  
  
### <a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> So erstellen Sie eine MFC‑Anwendung mit Debuginformationen für ausgewählte Module  
 Das Erstellen ausgewählter Module mit den MFC-Debugbibliotheken ermöglicht die schrittweise Ausführung der Module sowie die Verwendung weiterer Debugfunktionen. In den folgenden Schritten wird sowohl der Debug- als auch der Releasemodus des Visual C++-Makefile verwendet. Dadurch werden die im Folgenden beschriebenen Änderungen erforderlich. (Darüber hinaus ist die Option Alles neu erstellen erforderlich, wenn ein vollständiges Releasebuild benötigt wird.)  
  
1. Wählen Sie im Projektmappen-Explorer das Projekt aus.  
  
2. Wählen Sie im Menü **Ansicht** die Option **Eigenschaftenseiten**aus.  
  
3. Zunächst erstellen Sie eine neue Projektkonfiguration.  
  
   1. Klicken Sie im Dialogfeld **\<Projekt > Eigenschaftenseiten** auf die Schaltfläche **Konfigurations-Manager**.  
  
   2. Suchen Sie das Projekt im Raster des [Dialogfelds "Konfigurations-Manager"](https://msdn.microsoft.com/fa182dca-282e-4ae5-bf37-e155344ca18b). Wählen Sie in der Spalte **Konfiguration** die Option **\<Neu...>** aus.  
  
   3. Geben Sie im [Dialogfeld "Neue Projektkonfiguration"](https://msdn.microsoft.com/cca616dc-05a6-4fe3-bdc1-40c72a66f2be)im Feld **Projektkonfigurationsname** einen Namen für die neue Konfiguration ein, z. B. "Teildebugprojekt".  
  
   4. Wählen Sie in der Liste **Einstellungen kopieren von** die Option **Release**.  
  
   5. Klicken Sie auf **OK** , um das Dialogfeld **Neue Projektkonfiguration**zu schließen.  
  
   6. Schließen Sie das Dialogfeld **Konfigurations-Manager** .  
  
4. Nun legen Sie Optionen für das gesamte Projekt fest.  
  
   1. Wählen Sie im Dialogfeld **Eigenschaftenseiten** unter dem Ordner **Konfigurationseigenschaften** die Kategorie **Allgemein** aus.  
  
   2. Erweitern Sie im Raster für die Projekteinstellungen ggf. **Projektstandards** .  
  
   3. Suchen Sie unter **Projektstandards**die Option **Verwendung von MFC**. Die aktuelle Einstellung wird in der rechten Spalte des Rasters angezeigt. Klicken Sie auf die aktuelle Einstellung, und ändern Sie diese in **MFC in einer statischen Bibliothek verwenden**.  
  
   4. Öffnen Sie im linken Bereich des Dialogfelds **Eigenschaftenseiten** den Ordner **C/C++** , und wählen Sie **Präprozessor**aus. Suchen Sie im Eigenschaftsraster die Option **Präprozessordefinitionen** , und ersetzen Sie "NDEBUG" durch "_DEBUG".  
  
   5. Öffnen Sie im linken Bereich des Dialogfelds **Eigenschaftenseiten** den Ordner **Linker** , und wählen Sie die Kategorie **Eingabe** aus. Suchen Sie im Eigenschaftsraster die Option **Zusätzliche Abhängigkeiten**. Geben Sie in der Einstellung **Zusätzliche Abhängigkeiten** "NAFXCWD.LIB" und "LIBCMT" ein.  
  
   6. Klicken Sie auf **OK** , um die neuen Buildoptionen zu speichern und das Dialogfeld **Eigenschaftenseiten** zu schließen.  
  
5. Wählen Sie im Menü **Erstellen** die Option **Neu erstellen**. Dadurch werden alle Debuginformationen aus den Modulen entfernt, was sich jedoch nicht auf die MFC-Bibliothek auswirkt.  
  
6. Jetzt müssen Sie den ausgewählten Modulen in der Anwendung wieder Debuginformationen hinzufügen. Dabei ist zu beachten, dass das Festlegen von Haltepunkten und das Ausführen anderer Debuggerfunktionen nur in Modulen möglich ist, die mit Debuginformationen kompiliert wurden. Führen Sie die folgenden Schritte für jede Projektdatei aus, in der Debuginformationen enthalten sein sollen:  
  
   1. Öffnen Sie im Projektmappen-Explorer den Ordner **Quelldateien** unterhalb des Projekts.  
  
   2. Markieren Sie die Datei, für die Debuginformationen festgelegt werden sollen.  
  
   3. Wählen Sie im Menü **Ansicht** die Option **Eigenschaftenseiten**aus.  
  
   4. Öffnen Sie im Dialogfeld **Eigenschaftenseiten** unter dem Ordner **Konfigurationseinstellungen** den Ordner **C/C++** , und wählen Sie die Kategorie **Allgemein** aus.  
  
   5. Suchen Sie im Eigenschaftsraster die Option **Debuginformationsformat.**  
  
   6. Klicken Sie auf die Einstellungen **Debuginformationsformat** , und wählen sie die für die Debuginformationen gewünschte Option (gewöhnlich **/ZI**) aus.  
  
   7. Wenn Sie eine mit dem Anwendungs-Assistenten generierte Anwendung oder vorkompilierte Header verwenden, müssen Sie die vorkompilierten Header entweder deaktivieren oder erneut kompilieren, bevor Sie die anderen Module kompilieren. Andernfalls werden die Warnung C4650 und die Fehlermeldung C2855 ausgegeben. Sie können vorkompilierte Header deaktivieren, indem Sie im Dialogfeld **Eigenschaften von \<Projekt>** (Ordner **Konfigurationseigenschaften**, Unterordner **C/C++**, Kategorie **Vorkompilierte Header**) die Einstellung **Vorkompilierten Header erstellen/verwenden** ändern.  
  
7. Klicken Sie im Menü **Erstellen** auf **Erstellen** , um veraltete Projektdateien neu zu erstellen.  
  
   Alternativ zu dem in diesem Thema beschriebenen Verfahren können Sie auch ein externes Makefile verwenden, um die einzelnen Optionen für jede Datei zu definieren. In diesem Fall muss zum Herstellen einer Verknüpfung mit den MFC-Debugbibliotheken ein [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) -Flag für jedes Modul definiert werden. Wenn Sie die MFC-Releasebibliotheken verwenden möchten, muss NDEBUG definiert sein. Weitere Informationen über das Schreiben von externen Makefiles finden Sie in der [NMAKE-Referenz](https://msdn.microsoft.com/library/0421104d-8b7b-4bf3-86c1-928d9b7c1a8c).  
  
   [Inhalt](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Visual C++](../debugger/debugging-native-code.md)

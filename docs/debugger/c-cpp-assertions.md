---
title: C/C++-Assertionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c91ff9d752e2043829b3ea310606a9d8b82b1e1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845991"
---
# <a name="cc-assertions"></a>C/C++-Assertionen
Eine Assertionsanweisung formuliert eine Bedingung, die an einer bestimmten Stelle im Programm "true" lauten muss. Wenn diese Bedingung nicht wahr ist, schlägt die Assertion fehl, die programmausführung wird unterbrochen, und die [Dialogfeld Assertionsfehler](../debugger/assertion-failed-dialog-box.md) angezeigt wird.  

 Visual C++ unterstützt Assertionsanweisungen, die auf folgenden Konstrukten basieren:  

- MFC-Assertionen für MFC-Programme  

- [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) für Programme, die ATL verwenden.  

- CRT-Assertionen für Programme, die die C-Laufzeitbibliothek verwenden.  

- ANSI [assert-Funktion](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) für andere C/C++-Programme.  

  Sie können Assertionen verwenden, um logische Fehler zu erfassen, Ergebnisse einer Operation zu überprüfen und Fehlerbedingungen zu testen, die bearbeitet werden müssten.  

##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [Funktionsweise von Assertionen](#BKMK_How_assertions_work)  

 [Assertionen in Debug- und Releasebuilds](#BKMK_Assertions_in_Debug_and_Release_builds)  

 [Nebeneffekte der Verwendung von Assertionen](#BKMK_Side_effects_of_using_assertions)  

 [CRT-Assertionen](#BKMK_CRT_assertions)  

 [MFC-Assertionen](#BKMK_MFC_assertions)  

- [MFC-ASSERT_VALID und CObject:: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  

- [Einschränkungen von "AssertValid"](#BKMK_Limitations_of_AssertValid)  

  [Verwenden von Assertionen](#BKMK_Using_assertions)  

- [Erfassen von logischen Fehlern](#BKMK_Catching_logic_errors)  

- [Überprüfen der Ergebnisse](#BKMK_Checking_results_)  

- [Suchen von unbehandelten Fehlern](#BKMK_Testing_error_conditions_)  

##  <a name="BKMK_How_assertions_work"></a> Funktionsweise von Assertionen  
 Wenn der Debugger ein Programm aufgrund einer Assertion von MFC oder der C-Laufzeitbibliothek anhält, navigiert er zu der Stelle in der Quelldatei (sofern vorhanden), an der die Assertion aufgetreten ist. Die assertionsmeldung wird sowohl die [Fenster "Ausgabe"](../ide/reference/output-window.md) und **Assertionsfehler** Dialogfeld. Sie können die assertionsmeldung aus Kopieren der **Ausgabe** Fenster aus, um ein Textfenster angezeigt, wenn es für die zukünftige Verwendung gespeichert werden soll. Die **Ausgabe** kann auch andere Fehlermeldungen enthalten. Überprüfen Sie diese Meldungen sorgfältig; häufig enthalten sie Hinweise auf die Ursache des Assertionsfehlers.  

 Verwenden Sie Assertionen, um Fehler während der Entwicklung zu erkennen. Verwenden Sie im Allgemeinen eine Assertion für die jeweilige Annahme. Wenn Sie beispielsweise annehmen, dass ein Argument ungleich NULL ist, verwenden Sie eine Assertion, um diese Annahme zu testen.  

 [Inhalt](#BKMK_In_this_topic)  

##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Assertionen in Debug- und Releasebuilds  
 Assertionsanweisungen werden nur kompiliert, wenn `_DEBUG` definiert ist. Andernfalls behandelt der Compiler Assertionen als NULL-Anweisungen. Assertionsanweisungen verursachen daher keinen Mehraufwand und keine Leistungseinbußen in der endgültigen Programmversion, sodass Sie keine `#ifdef`-Anweisungen verwenden müssen.  

##  <a name="BKMK_Side_effects_of_using_assertions"></a> Nebeneffekte der Verwendung von Assertionen  
 Wenn Sie Assertionen in den Code einfügen, sollten Sie sicherstellen, dass die Assertionen keine Nebeneffekte haben. Betrachten Sie beispielsweise die folgende Assertion, mit der der `nM`-Wert geändert wird:  

```cpp
ASSERT(nM++ > 0); // Don't do this!  
```  

 Da der `ASSERT`-Ausdruck in der Releaseversion des Programms nicht ausgewertet wird, verfügt `nM` in der Debug- und Releaseversion über unterschiedliche Werte. Um dieses Problem in MFC zu vermeiden, können Sie die [überprüfen](/cpp/mfc/reference/diagnostic-services#verify) -Makro anstelle von `ASSERT`.  `VERIFY` Wertet den Ausdruck in allen Versionen, aber nicht das Ergebnis in der endgültigen Produktversion.  

 Da die Auswertung einer Funktion unerwartete Nebeneffekte haben kann, sollten Funktionsaufrufe in Assertionsanweisungen mit Vorsicht verwendet werden.  

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  

 `VERIFY` ruft `myFnctn` sowohl in der Debug- als auch in der Releaseversion auf und kann somit verwendet werden. Durch die Verwendung von `VERIFY` wird jedoch ein Mehraufwand aufgrund eines unnötigen Funktionsaufrufs in der Releaseversion verursacht.  

 [Inhalt](#BKMK_In_this_topic)  

##  <a name="BKMK_CRT_assertions"></a> CRT-Assertionen  
 Die CRTDBG.H. H-Headerdatei definiert die [_ASSERT "und" _ASSERTE-Makros](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) zur Überprüfung von Assertionen.  


| Makro | Ergebnis |
|------------| - |
| `_ASSERT` | Dateiname und Zeilennummer von `_ASSERT`, wenn der angegebene Ausdruck mit FALSE ausgewertet wird. |
| `_ASSERTE` | Identisch mit `_ASSERT`, zusätzlich jedoch eine Zeichenfolgenentsprechung des Ausdrucks, für den die Assertion ausgeführt wurde. |

 `_ASSERTE` ist leistungsfähiger, da der überwachte Ausdruck gemeldet wird, wenn er mit FALSE ausgewertet wurde. Auf diese Weise lässt sich das Problem u. U. bereits ohne Zuhilfenahme des Quellcodes identifizieren. In der Debugversion der Anwendung ist jedoch für jeden mit `_ASSERTE` überprüften Ausdruck eine Zeichenfolgenkonstante enthalten. Bei Verwendung vieler `_ASSERTE`-Makros können diese Zeichenfolgenausdrücke beträchtlichen Speicherplatz belegen. Falls dies zu Problemen führt, verwenden Sie `_ASSERT`, um Speicherplatz zu sparen.  

 Wenn `_DEBUG` definiert ist, wird das `_ASSERTE`-Makro wie folgt definiert:  

```cpp
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  

 Wenn der überwachte Ausdruck FALSE ergibt, wird [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) wird aufgerufen, um den Assertionsfehler (standardmäßig ein Meldungsdialogfeld mit) gemeldet. Auf Wunsch **wiederholen** in das Meldungsdialogfeld `_CrtDbgReport` gibt 1 zurück, und `_CrtDbgBreak` ruft der Debugger über `DebugBreak`.  

### <a name="checking-for-heap-corruption"></a>Überprüfen des Heaps auf Beschädigungen  
 Im folgenden Beispiel wird [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) des Heaps auf Beschädigungen zu überprüfen:  

```cpp
_ASSERTE(_CrtCheckMemory());  
```  

### <a name="checking-pointer-validity"></a>Überprüfen der Gültigkeit von Zeigern  
 Im folgenden Beispiel wird [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) um sicherzustellen, dass für ein bestimmten Speicherbereich für Lese- und Schreibvorgänge gültig ist.  

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  

 Im folgenden Beispiel wird [_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) , ob ein Zeiger auf den Speicher im lokalen Heap zeigt (der Heap erstellt und verwaltet, die von dieser Instanz von der C-Laufzeitbibliothek – eine DLL-Datei haben eine eigene Instanz von der Bibliothek, und daher einen eigenen Heap außerhalb des anwendungsheaps). Diese Assertion erkennt nicht nur NULL-Adressen oder Adressen außerhalb des gültigen Bereichs, sondern auch Zeiger auf statische Variablen, Stapelvariablen und sonstigen nicht lokalen Speicher.  

```cpp
_ASSERTE(_CrtIsValidPointer( myData );  
```  

### <a name="checking-a-memory-block"></a>Überprüfen eines Speicherblocks  
 Im folgenden Beispiel wird [_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) , stellen Sie sicher, dass ein Speicherblock im lokalen Heap befindet und einen gültigen Blocktyp.  

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  

 [Inhalt](#BKMK_In_this_topic)  

##  <a name="BKMK_MFC_assertions"></a> MFC-Assertionen  
 MFC definiert die [ASSERT](https://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) Makros zur Überprüfung von Assertionen. Sie definiert auch die `MFC ASSERT_VALID`- und `CObject::AssertValid`-Methoden zum Überprüfen des internen Zustands eines von `CObject` abgeleiteten Objekts.  

 Wenn das Argument des MFC-`ASSERT`-Makros mit "0 (null)" oder "false" ausgewertet wird, wird die Programmausführung durch das Makro angehalten und eine Warnung an den Benutzer ausgegeben. Andernfalls wird die Ausführung fortgesetzt.  

 Wenn eine Assertion fehlschlägt, werden der Name der Quelldatei sowie die Zeilennummer der Assertion in einem Meldungsdialogfeld angezeigt. Bei Auswahl von "Wiederholen" im Dialogfeld ""-Feld, einen Aufruf von [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) wird die Ausführung an den Debugger zu unterbrechen. An diesem Punkt können Sie die Aufrufliste und weitere Debuggerfunktionen überprüfen, um die Ursache für den Assertionsfehler zu ermitteln. Wenn Sie aktiviert haben [Just-in-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md), und der Debugger nicht bereits ausgeführt wurde, wird das Dialogfeld kann der Debugger.  

 Das folgende Beispiel veranschaulicht die Verwendung von `ASSERT`, um den Rückgabewert einer Funktion zu überprüfen:  

```cpp
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  

 Können Sie ASSERT mit der [IsKindOf](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#iskindof) der Funktion für die typüberprüfung der Funktionsargumente:  

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  

 In der Releaseversion generiert das `ASSERT`-Makro keinen Code. Wenn Sie den Ausdruck in der Releaseversion auswerten müssen, verwenden Sie die [überprüfen](https://msdn.microsoft.com/library/s8c29sw2.aspx#verify) Makro anstelle ASSERT.  

###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC-ASSERT_VALID und CObject:: AssertValid  
 Die [CObject:: AssertValid](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#assertvalid) Methode bietet den internen Zustand eines Objekts laufzeitüberprüfungen. Es ist zwar nicht erforderlich, `AssertValid`beim Ableiten der Klasse aus `CObject` zu überschreiben, Sie können so jedoch die Zuverlässigkeit der Klasse erhöhen. `AssertValid` sollte Assertionen für alle Membervariablen des Objekts ausführen und sicherstellen, dass diese gültige Werte enthalten. Beispielsweise sollte überprüft werden, ob alle Membervariablen in Form von Zeigern ungleich NULL sind.  

 Im folgenden Beispiel wird die Deklaration einer `AssertValid`-Funktion erläutert:  

```cpp
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  
```  

 Wenn Sie `AssertValid` überschreiben, rufen Sie die Basisklassenversion von `AssertValid` auf, bevor Sie eigene Überprüfungen vornehmen. Überprüfen Sie dann mit dem ASSERT-Makro wie folgt die Gültigkeit der Member, die nur in der abgeleiteten Klasse vorkommen:  

```cpp
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  

    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  
```  

 Wenn durch eine der Membervariablen Objekte gespeichert werden, können Sie deren interne Gültigkeit mit dem `ASSERT_VALID`-Makro testen (falls die betreffende Klasse `AssertValid` überschreibt).  

 Betrachten Sie beispielsweise eine Klasse `CMyData`, welche Geschäfte einer [CObList](/cpp/mfc/reference/coblist-class) in einem der zugehörigen Membervariablen. Die `CObList`-Variable `m_DataList` speichert eine Auflistung von `CPerson`-Objekten. Die Deklaration von `CMyData` lautet in den wesentlichen Teilen wie folgt:  

```cpp
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  
```  

 Die `AssertValid`-Überschreibung in `CMyData` sieht wie folgt aus:  

```cpp
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  
```  

 `CMyData` verwendet den `AssertValid`-Mechanismus, um die Gültigkeit der in ihrem Datenmember gespeicherten Objekte zu testen. Durch das `AssertValid`-Überschreiben von `CMyData` wird das `ASSERT_VALID`-Makro für die eigene m_pDataList-Membervariable aufgerufen.  

 Die Gültigkeitsüberprüfung wird auf dieser Ebene nicht beendet, da die `CObList`-Klasse auch von `AssertValid` überschrieben wird. Diese Überschreibung bewirkt weitere Gültigkeitsüberprüfungen des internen Listenzustands. Auf diese Weise führt eine Gültigkeitsüberprüfung für ein `CMyData`-Objekt zu weiteren Gültigkeitsüberprüfungen, mit denen der interne Zustand des gespeicherten `CObList`-Listenobjekts getestet wird.  

 Mit geringem Mehraufwand könnten die Gültigkeitsüberprüfungen auch auf die in der Liste gespeicherten `CPerson`-Objekte ausgeweitet werden. Sie könnten eine `CPersonList`-Klasse von `CObList` ableiten und `AssertValid` überschreiben. Hierbei würden Sie `CObject::AssertValid` aufrufen und dann die Liste durchlaufen, wobei für jedes in der Liste gespeicherte `AssertValid`-Objekt `CPerson` aufgerufen würde. Durch die am Anfang dieses Themas dargestellte `CPerson`-Klasse wird `AssertValid` bereits überschrieben.  

 Dieses Verfahren ist beim Erstellen von Debugbuilds äußerst hilfreich. Beim späteren Erstellen eines Releasebuilds wird das Verfahren automatisch deaktiviert.  

###  <a name="BKMK_Limitations_of_AssertValid"></a> Einschränkungen von "AssertValid"  
 Eine ausgelöste Assertion weist darauf hin, dass das Objekt mit Sicherheit fehlerhaft ist, und die Ausführung wird angehalten. Wird keine Assertion ausgelöst, so bedeutet dies jedoch nur, dass kein Problem festgestellt wurde, die Fehlerfreiheit des Objekts kann aber trotzdem nicht garantiert werden.  

 [Inhalt](#BKMK_In_this_topic)  

##  <a name="BKMK_Using_assertions"></a> Verwenden von Assertionen  

###  <a name="BKMK_Catching_logic_errors"></a> Erfassen von logischen Fehlern  
 So kann eine Assertion für eine Bedingung festgelegt werden, die entsprechend der Programmlogik true ergeben muss. Die Assertion bleibt so lange wirkungslos, bis ein logischer Fehler auftritt.  

 Angenommen, Sie simulieren die Bewegungen von Gasmolekülen in einem Behälter, und die `numMols`-Variable gibt die Gesamtanzahl der Moleküle an. Diese Zahl darf nie kleiner als 0 (null) sein, sodass Sie die folgende MFC-Assertionsanweisung einfügen können:  

```cpp
ASSERT(numMols >= 0);  
```  

 Sie können auch eine CRT-Assertion wie die folgende einschließen:  

```cpp
_ASSERT(numMols >= 0);  
```  

 Diese Anweisungen bleiben wirkungslos, solange das Programm einwandfrei funktioniert. Wenn ein logischer Fehler bewirkt, dass `numMols` um kleiner als NULL sein, jedoch die Assertion hält die Ausführung des Programms an und zeigt die [Dialogfeld zur Assertion Fehler](../debugger/assertion-failed-dialog-box.md).  

 [Inhalt](#BKMK_In_this_topic)  

###  <a name="BKMK_Checking_results_"></a> Überprüfen der Ergebnisse  
 Besonders eignen sich Assertionen zum Testen von Operationen, deren Ergebnisse durch einen schnellen Blick auf den Code nicht ersichtlich sind.  

 Dies ist beispielsweise beim folgenden Code der Fall, in dem die `iMols`-Variable abhängig vom Inhalt der verketteten Liste, auf die `mols` zeigt, aktualisiert wird.  

```cpp
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  

 Die Anzahl der von `iMols` gezählten Moleküle muss immer kleiner oder gleich `numMols`, d. h. der Gesamtanzahl der Moleküle, sein. Durch die visuelle Prüfung dieser Schleife kann nicht ermittelt werden, dass dies immer zutrifft, sodass diese Bedingung nach der Schleife mit einer Assertionsanweisung überprüft wird.  

 [Inhalt](#BKMK_In_this_topic)  

###  <a name="BKMK_Testing_error_conditions_"></a> Suchen von unbehandelten Fehlern  
 Assertionen ermöglichen es Ihnen, den Code an den Stellen, an denen alle Fehler bereits behandelt worden sein sollten, auf Fehlerzustände zu testen. Im folgenden Beispiel gibt eine Grafikroutine einen Fehlercode oder, bei erfolgreicher Ausführung, 0 (null) zurück.  

```cpp
myErr = myGraphRoutine(a, b);  

/* Code to handle errors and  
   reset myErr if successful */  

ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  

 Wenn der Fehlerbehandlungscode einwandfrei funktioniert, sollte der Fehler behandelt und `myErr` vor Erreichen der Assertion auf 0 (null) zurückgesetzt werden. Wenn `myErr` verfügt über einen anderen Wert, schlägt die Assertion fehl, das Programm wird angehalten, und die [Dialogfeld zur Assertion Fehler](../debugger/assertion-failed-dialog-box.md) angezeigt wird.  

 Assertionsanweisungen sind allerdings kein Ersatz für Fehlerbehandlungscode. So kann die Assertionsanweisung im folgenden Beispiel im Releaseversionscode u. U. Probleme bereiten:  

```cpp
myErr = myGraphRoutine(a, b);  

/* No Code to handle errors */  

ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  

 Bei diesem Code wird davon ausgegangen, dass der Fehlerzustand durch die Assertionsanweisung behandelt wird. Dies würde im endgültigen Releasecode dazu führen, dass alle von `myGraphRoutine` zurückgegebenen Fehlercodes nicht behandelt würden.  

 [Inhalt](#BKMK_In_this_topic)  

## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md)

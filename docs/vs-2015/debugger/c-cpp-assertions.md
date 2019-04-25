---
title: C / C++-Assertionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 759376a6682287cbe41d4d1dc13666c5a540f8e9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050556"
---
# <a name="cc-assertions"></a>C/C++-Assertionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Assertionsanweisung formuliert eine Bedingung, die an einer bestimmten Stelle im Programm "true" lauten muss. Wenn diese Bedingung nicht den Wert TRUE aufweist, kann die Assertion nicht durchgeführt werden, die Programmausführung wird unterbrochen, und das Dialogfeld [Assertionsfehler](../debugger/assertion-failed-dialog-box.md) wird geöffnet.  

 Visual C++ unterstützt Assertionsanweisungen, die auf folgenden Konstrukten basieren:  

- MFC-Assertionen für MFC-Programme  

- [ATLASSERT](http://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3) für Programme, die ATL verwenden.  

- CRT-Assertionen für Programme, die die C-Laufzeitbibliothek verwenden.  

- Die ANSI-[assert-Funktion](http://msdn.microsoft.com/library/a9ca031a-648b-47a6-bdf1-65fc7399dd40) für andere C/C++‑Programme.  

  Sie können Assertionen verwenden, um logische Fehler zu erfassen, Ergebnisse einer Operation zu überprüfen und Fehlerbedingungen zu testen, die bearbeitet werden müssten.  

## <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [Funktionsweise von Assertionen](#BKMK_How_assertions_work)  

 [Assertionen in Debug- und Versionsbuilds](#BKMK_Assertions_in_Debug_and_Release_builds)  

 [Nebeneffekte der Verwendung von Assertionen](#BKMK_Side_effects_of_using_assertions)  

 [CRT-Assertionen](#BKMK_CRT_assertions)  

 [MFC-Assertionen](#BKMK_MFC_assertions)  

- [MFC ASSERT_VALID und CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  

- [Einschränkungen von AssertValid](#BKMK_Limitations_of_AssertValid)  

  [Verwenden von Assertionen](#BKMK_Using_assertions)  

- [Erfassen von logischen Fehlern](#BKMK_Catching_logic_errors)  

- [Überprüfen der Ergebnisse](#BKMK_Checking_results_)  

- [Suchen von unbehandelten Fehlern](#BKMK_Testing_error_conditions_)  

## <a name="BKMK_How_assertions_work"></a> Funktionsweise von Assertionen  
 Wenn der Debugger ein Programm aufgrund einer Assertion von MFC oder der C-Laufzeitbibliothek anhält, navigiert er zu der Stelle in der Quelldatei (sofern vorhanden), an der die Assertion aufgetreten ist. Die Assertionsmeldung wird sowohl im [Ausgabefenster](../ide/reference/output-window.md) als auch im Dialogfeld **Assertionsfehler** angezeigt. Sie können die Assertionsmeldung aus dem **Ausgabefenster** in ein Textfenster kopieren, wenn Sie sie zu Referenzzwecken behalten möchten. Das **Ausgabefenster** enthält u.U. weitere Fehlermeldungen. Überprüfen Sie diese Meldungen sorgfältig; häufig enthalten sie Hinweise auf die Ursache des Assertionsfehlers.  

 Verwenden Sie Assertionen, um Fehler während der Entwicklung zu erkennen. Verwenden Sie im Allgemeinen eine Assertion für die jeweilige Annahme. Wenn Sie beispielsweise annehmen, dass ein Argument ungleich NULL ist, verwenden Sie eine Assertion, um diese Annahme zu testen.  

 [Inhalt](#BKMK_In_this_topic)  

## <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Assertionen in Debug- und Versionsbuilds  
 Assertionsanweisungen werden nur kompiliert, wenn `_DEBUG` definiert ist. Andernfalls behandelt der Compiler Assertionen als NULL-Anweisungen. Assertionsanweisungen verursachen daher keinen Mehraufwand und keine Leistungseinbußen in der endgültigen Programmversion, sodass Sie keine `#ifdef`-Direktiven verwenden müssen.  

## <a name="BKMK_Side_effects_of_using_assertions"></a> Nebeneffekte der Verwendung von Assertionen  
 Wenn Sie Assertionen in den Code einfügen, sollten Sie sicherstellen, dass die Assertionen keine Nebeneffekte haben. Betrachten Sie beispielsweise die folgende Assertion, mit der der `nM`-Wert geändert wird:  

```  
ASSERT(nM++ > 0); // Don't do this!  

```  

 Da der `ASSERT`-Ausdruck in der Releaseversion des Programms nicht ausgewertet wird, verfügt `nM` in der Debug- und Releaseversion über unterschiedliche Werte. Um dieses Problem in MFC zu vermeiden, können Sie die [überprüfen](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) -Makro anstelle von `ASSERT`.  `VERIFY` Wertet den Ausdruck in allen Versionen, aber nicht das Ergebnis in der endgültigen Produktversion.  

 Da die Auswertung einer Funktion unerwartete Nebeneffekte haben kann, sollten Funktionsaufrufe in Assertionsanweisungen mit Vorsicht verwendet werden.  

```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  

 `VERIFY` ruft `myFnctn` sowohl in der Debug- als auch in der Releaseversion auf und kann somit verwendet werden. Durch die Verwendung von `VERIFY` wird jedoch ein Mehraufwand aufgrund eines unnötigen Funktionsaufrufs in der Releaseversion verursacht.  

 [Inhalt](#BKMK_In_this_topic)  

## <a name="BKMK_CRT_assertions"></a> CRT-Assertionen  
 Die Headerdatei „CRTDBG.H“ enthält Definitionen der [Makros _ASSERT und _ASSERTE](http://msdn.microsoft.com/library/e98fd2a6-7f5e-4aa8-8fe8-e93490deba36), die zur Überprüfung von Assertionen verwendet werden.  

|   Makro    |                                             Ergebnis                                              |
|------------|-------------------------------------------------------------------------------------------------|
| `_ASSERT`  | Dateiname und Zeilennummer von `_ASSERT`, wenn der angegebene Ausdruck mit FALSE ausgewertet wird. |
| `_ASSERTE` |      Identisch mit `_ASSERT`, zusätzlich jedoch eine Zeichenfolgenentsprechung des Ausdrucks, für den die Assertion ausgeführt wurde.       |

 `_ASSERTE` ist leistungsfähiger, da der überwachte Ausdruck gemeldet wird, wenn er mit FALSE ausgewertet wurde. Auf diese Weise lässt sich das Problem u. U. bereits ohne Zuhilfenahme des Quellcodes identifizieren. In der Debugversion der Anwendung ist jedoch für jeden mit `_ASSERTE` überprüften Ausdruck eine Zeichenfolgenkonstante enthalten. Bei Verwendung vieler `_ASSERTE`-Makros können diese Zeichenfolgenausdrücke beträchtlichen Speicherplatz belegen. Falls dies zu Problemen führt, verwenden Sie `_ASSERT`, um Speicherplatz zu sparen.  

 Wenn `_DEBUG` definiert ist, wird das `_ASSERTE`-Makro wie folgt definiert:  

```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  

 Wenn der Ausdruck bei der Assertionsauswertung FALSE ergibt, wird [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) aufgerufen und gibt den Assertionsfehler (standardmäßig in einem Meldungsdialogfeld) aus. Wenn Sie im Meldungsdialogfeld **Wiederholen** auswählen, gibt `_CrtDbgReport` den Wert 1 zurück, und `_CrtDbgBreak` ruft den Debugger über `DebugBreak` auf.  

### <a name="checking-for-heap-corruption"></a>Überprüfen des Heaps auf Beschädigungen  
 Im folgenden Beispiel wird [_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765) verwendet, um den Heap auf Beschädigungen zu überprüfen:  

```  
_ASSERTE(_CrtCheckMemory());  
```  

### <a name="checking-pointer-validity"></a>Überprüfen der Gültigkeit von Zeigern  
 Im folgenden Beispiel wird anhand von [_CrtIsValidPointer](http://msdn.microsoft.com/library/91c35590-ea5e-450f-a15d-ad8d62ade1fa) überprüft, ob in einen bestimmten Speicherbereich geschrieben bzw. daraus gelesen werden kann.  

```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  

 Im folgenden Beispiel wird anhand von [_CrtIsValidHeapPointer](http://msdn.microsoft.com/library/caf597ce-1b05-4764-9f37-0197a982bec5) überprüft, ob ein Zeiger auf Speicher im lokalen Heap zeigt. (Es handelt sich um den Heap, der von dieser Instanz der C-Laufzeitbibliothek generiert und verwaltet wird. Eine DLL kann über eine eigene Bibliotheksinstanz und daher auch über einen eigenen Heap außerhalb des Anwendungsheaps verfügen.) Diese Assertion erkennt nicht nur NULL-Adressen oder Adressen außerhalb des gültigen Bereichs, sondern auch Zeiger auf statische Variablen, Stapelvariablen und sonstigen nicht lokalen Speicher.  

```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  

### <a name="checking-a-memory-block"></a>Überprüfen eines Speicherblocks  
 Im folgenden Beispiel wird anhand von [_CrtIsMemoryBlock](http://msdn.microsoft.com/library/f7cbbc60-3690-4da0-a07b-68fd7f250273) sichergestellt, dass ein Speicherblock sich im lokalen Heap befindet und über einen gültigen Blocktyp verfügt.  

```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  

 [Inhalt](#BKMK_In_this_topic)  

## <a name="BKMK_MFC_assertions"></a> MFC-Assertionen  
 Das [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)-Makro für die Assertionsüberprüfung ist in MFC definiert. Sie definiert auch die `MFC ASSERT_VALID`- und `CObject::AssertValid`-Methoden zum Überprüfen des internen Zustands eines von `CObject` abgeleiteten Objekts.  

 Wenn das Argument des MFC-`ASSERT`-Makros mit "0 (null)" oder "false" ausgewertet wird, wird die Programmausführung durch das Makro angehalten und eine Warnung an den Benutzer ausgegeben. Andernfalls wird die Ausführung fortgesetzt.  

 Wenn eine Assertion fehlschlägt, werden der Name der Quelldatei sowie die Zeilennummer der Assertion in einem Meldungsdialogfeld angezeigt. Wenn Sie im Dialogfeld auf „Wiederholen“ klicken, wird [AfxDebugBreak](http://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) aufgerufen, die Ausführung unterbrochen und der Debugger aufgerufen. An diesem Punkt können Sie die Aufrufliste und weitere Debuggerfunktionen überprüfen, um die Ursache für den Assertionsfehler zu ermitteln. Bei Aktivierung von [Just-In-Time-Debugging](../debugger/just-in-time-debugging-in-visual-studio.md) kann der Debugger über das Dialogfeld aufgerufen werden, sofern er nicht bereits ausgeführt wurde.  

 Das folgende Beispiel veranschaulicht die Verwendung von `ASSERT`, um den Rückgabewert einer Funktion zu überprüfen:  

```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  

 Um eine Typüberprüfung für die Funktionsargumente vorzunehmen, können Sie ASSERT mit der [IsKindOf](http://msdn.microsoft.com/library/7c87c748-b7e0-4c6d-9694-6035e62fdfd6)-Funktion verwenden:  

```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  

 In der Releaseversion generiert das `ASSERT`-Makro keinen Code. Wenn Sie den Ausdruck in der Releaseversion auswerten müssen, verwenden Sie anstelle von ASSERT das [VERIFY](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96)-Makro.  

### <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID und CObject::AssertValid  
 Die [CObject::AssertValid](http://msdn.microsoft.com/library/534a0744-4ab6-423d-b492-b4058b3d5157)-Methode ermöglicht es, den internen Zustand eines Objekts zur Laufzeit zu überprüfen. Es ist zwar nicht erforderlich, `AssertValid`beim Ableiten der Klasse aus `CObject` zu überschreiben, Sie können so jedoch die Zuverlässigkeit der Klasse erhöhen. `AssertValid` sollte Assertionen für alle Membervariablen des Objekts ausführen und sicherstellen, dass diese gültige Werte enthalten. Beispielsweise sollte überprüft werden, ob alle Membervariablen in Form von Zeigern ungleich NULL sind.  

 Im folgenden Beispiel wird die Deklaration einer `AssertValid`-Funktion erläutert:  

```  
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

```  
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

 Durch die `CMyData`-Klasse wird beispielsweise [CObList](http://msdn.microsoft.com/library/80699c93-33d8-4f8b-b8cf-7b58aeab64ca) in einer ihrer Membervariablen gespeichert. Die `CObList`-Variable `m_DataList` speichert eine Auflistung von `CPerson`-Objekten. Die Deklaration von `CMyData` lautet in den wesentlichen Teilen wie folgt:  

```  
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

```  
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

 `CMyData` verwendet den `AssertValid`-Mechanismus, um die Gültigkeit der im Datenmember gespeicherten Objekte zu testen. Durch das `AssertValid`-Überschreiben von `CMyData` wird das `ASSERT_VALID`-Makro für die eigene m_pDataList-Membervariable aufgerufen.  

 Die Gültigkeitsüberprüfung wird auf dieser Ebene nicht beendet, da die `CObList`-Klasse auch von `AssertValid` überschrieben wird. Diese Überschreibung bewirkt weitere Gültigkeitsüberprüfungen des internen Listenzustands. Auf diese Weise führt eine Gültigkeitsüberprüfung für ein `CMyData`-Objekt zu weiteren Gültigkeitsüberprüfungen, mit denen der interne Zustand des gespeicherten `CObList`-Listenobjekts getestet wird.  

 Mit geringem Mehraufwand könnten die Gültigkeitsüberprüfungen auch auf die in der Liste gespeicherten `CPerson`-Objekte ausgeweitet werden. Sie könnten eine `CPersonList`-Klasse von `CObList` ableiten und `AssertValid` überschreiben. Hierbei würden Sie `CObject::AssertValid` aufrufen und dann die Liste durchlaufen, wobei für jedes in der Liste gespeicherte `AssertValid`-Objekt `CPerson` aufgerufen würde. Durch die am Anfang dieses Themas dargestellte `CPerson`-Klasse wird `AssertValid` bereits überschrieben.  

 Dieses Verfahren ist beim Erstellen von Debugbuilds äußerst hilfreich. Beim späteren Erstellen eines Releasebuilds wird das Verfahren automatisch deaktiviert.  

### <a name="BKMK_Limitations_of_AssertValid"></a> Einschränkungen von AssertValid  
 Eine ausgelöste Assertion weist darauf hin, dass das Objekt mit Sicherheit fehlerhaft ist, und die Ausführung wird angehalten. Wird keine Assertion ausgelöst, so bedeutet dies jedoch nur, dass kein Problem festgestellt wurde, die Fehlerfreiheit des Objekts kann aber trotzdem nicht garantiert werden.  

 [Inhalt](#BKMK_In_this_topic)  

## <a name="BKMK_Using_assertions"></a> Verwenden von Assertionen  

### <a name="BKMK_Catching_logic_errors"></a> Erfassen von logischen Fehlern  
 So kann eine Assertion für eine Bedingung festgelegt werden, die entsprechend der Programmlogik true ergeben muss. Die Assertion bleibt so lange wirkungslos, bis ein logischer Fehler auftritt.  

 Angenommen, Sie simulieren die Bewegungen von Gasmolekülen in einem Behälter, und die `numMols`-Variable gibt die Gesamtanzahl der Moleküle an. Diese Zahl darf nie kleiner als 0 (null) sein, sodass Sie die folgende MFC-Assertionsanweisung einfügen können:  

```  
ASSERT(numMols >= 0);  

```  

 Sie können auch eine CRT-Assertion wie die folgende einschließen:  

```  
_ASSERT(numMols >= 0);  
```  

 Diese Anweisungen bleiben wirkungslos, solange das Programm einwandfrei funktioniert. Wenn ein logischer Fehler bewirkt, dass `numMols` um kleiner als NULL sein, jedoch die Assertion hält die Ausführung des Programms an und zeigt die [Dialogfeld zur Assertion Fehler](../debugger/assertion-failed-dialog-box.md).  

 [Inhalt](#BKMK_In_this_topic)  

### <a name="BKMK_Checking_results_"></a> Überprüfen der Ergebnisse  
 Besonders eignen sich Assertionen zum Testen von Operationen, deren Ergebnisse durch einen schnellen Blick auf den Code nicht ersichtlich sind.  

 Dies ist beispielsweise beim folgenden Code der Fall, in dem die `iMols`-Variable abhängig vom Inhalt der verketteten Liste, auf die `mols` zeigt, aktualisiert wird.  

```  
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

### <a name="BKMK_Testing_error_conditions_"></a> Suchen von unbehandelten Fehlern  
 Assertionen ermöglichen es Ihnen, den Code an den Stellen, an denen alle Fehler bereits behandelt worden sein sollten, auf Fehlerzustände zu testen. Im folgenden Beispiel gibt eine Grafikroutine einen Fehlercode oder, bei erfolgreicher Ausführung, 0 (null) zurück.  

```  
myErr = myGraphRoutine(a, b);  

/* Code to handle errors and  
   reset myErr if successful */  

ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  

 Wenn der Fehlerbehandlungscode einwandfrei funktioniert, sollte der Fehler behandelt und `myErr` vor Erreichen der Assertion auf 0 (null) zurückgesetzt werden. Wenn `myErr` verfügt über einen anderen Wert, schlägt die Assertion fehl, das Programm wird angehalten, und die [Dialogfeld zur Assertion Fehler](../debugger/assertion-failed-dialog-box.md) angezeigt wird.  

 Assertionsanweisungen sind allerdings kein Ersatz für Fehlerbehandlungscode. So kann die Assertionsanweisung im folgenden Beispiel im Releasecode u. U. Probleme bereiten:  

```  
myErr = myGraphRoutine(a, b);  

/* No Code to handle errors */  

ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  

 Bei diesem Code wird davon ausgegangen, dass der Fehlerzustand durch die Assertionsanweisung behandelt wird. Dies würde im Releaseversionscode dazu führen, dass alle von `myGraphRoutine` zurückgegebenen Fehlercodes nicht behandelt würden.  

 [Inhalt](#BKMK_In_this_topic)  

## <a name="see-also"></a>Siehe auch  
 [Debugger Security (Debuggersicherheit)](../debugger/debugger-security.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md)

---
title: Empfohlene Vorgehensweisen und Beispiele (SAL) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1d5daf0f5d79683b3c6ef7f97d5f5113d294f6ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-and-examples-sal"></a>Empfohlene Vorgehensweisen und Beispiele (SAL)
Es gibt folgende Möglichkeiten Out Source Code Annotation Language (SAL) nutzen und einige der häufigsten Probleme zu vermeiden.  
  
## <a name="in"></a>_In\_  
 Wenn die Funktion auf das Element schreiben soll, verwenden `_Inout_` anstelle von `_In_`. Dies ist besonders in Fällen, die automatische Konvertierung von älteren Makros zu SAL relevant. Vor dem SAL, viele Programmierer Makros als Kommentare verwendet – Makros, die mit dem Namen wurden `IN`, `OUT`, `IN_OUT`, oder Varianten dieser Namen. Jedoch wir empfehlen, dass Sie diese Makros in SAL konvertieren, dringend auch große Sorgfalt geboten, wenn Sie konvertiert werden, da der Code möglicherweise geändert wurden, da der ursprüngliche Prototyp geschrieben wurde und das alte Makro möglicherweise nicht mehr wieder der Code. Achten Sie insbesondere die `OPTIONAL` Makro kommentieren, da sie häufig falsch platziert wird – z. B. auf der falschen Seite einem Komma.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ int *p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
// Correct  
void Func2(_Inout_ PCHAR p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
```  
  
## <a name="opt"></a>_opt\_  
 Wenn der Aufrufer nicht zulässig ist, um einen null-Zeiger zu übergeben, verwenden Sie `_In_` oder `_Out_` anstelle von `_In_opt_` oder `_Out_opt_`. Dies gilt auch für eine Funktion, die überprüft ihre Parameter und gibt einen Fehler zurück, wenn er NULL ist, wenn es nicht sein sollte. Obwohl mit einer Funktion unerwarteten NULL Parameter überprüfen und zurückgeben ordnungsgemäß ein guter Programmierstil defensiven ist, es bedeutet nicht, dass die parameteranmerkung ein optionaler Typ sein kann (_*Xxx*_opt\_).  
  
```cpp  
  
// Incorrect  
void Func1(_Out_opt_ int *p1)  
{  
    *p = 1;  
}  
  
// Correct  
void Func2(_Out_ int *p1)  
{  
    *p = 1;  
}  
  
```  
  
## <a name="predefensive-and-postdefensive"></a>_Pre_defensive\_ und _Post_defensive\_  
 Wenn eine Funktion eine Vertrauensgrenze angezeigt wird, empfehlen wir die Verwendung der `_Pre_defensive_` Anmerkung.  Die Modifizierer "defensive" ändert bestimmte Anmerkungen, die zum Zeitpunkt der Aufruf an, die Schnittstelle sollte unbedingt überprüft werden, aber in implementierungstext sollten davon ausgehen, dass möglicherweise falsche Parameter übergeben werden. In diesem Fall `_In_ _Pre_defensive_` wird an eine Vertrauensgrenze, um anzugeben, dass, obwohl ein Aufrufer ein Fehler angezeigt wird, wenn er versucht, übergeben Sie NULL, Hauptteil der Funktion analysiert werden, als ob der Parameter NULL, und jeder Versuch, die Zeiger ohne vorherige dereferenzieren möglicherweise bevorzugt Überprüfen es auf NULL wird angezeigt.  Ein `_Post_defensive_` Anmerkung ist auch verfügbar, für die Verwendung in Rückrufen, in dem die vertrauenswürdigen Partei wird davon ausgegangen, dass der Aufrufer und der nicht vertrauenswürdige Code wird der Code bezeichnet.  
  
## <a name="outwrites"></a>_Out_writes\_  
 Das folgende Beispiel zeigt eine allgemeine unsachgemäße Verwendung des `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 Die Anmerkung `_Out_writes_` gibt an, dass Sie einen Puffer haben. Es wurde `cb` Bytes belegt, mit dem ersten Byte bei Funktionsende initialisiert. Diese Anmerkung ist nicht streng falsche, und es ist hilfreich, die die zugeordnete Größe express. Allerdings ist es nicht mitteilen, wie viele Elemente von der Funktion initialisiert werden.  
  
 Das nächste Beispiel zeigt die richtige dreifach, um die genaue Größe des initialisierten Teils des Puffers vollständig anzugeben.  
  
```cpp  
  
// Correct  
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,   
    DWORD size,  
    PDWORD pCount  
);  
  
void Func2(_Out_writes_all_(size) CHAR *pb,   
    DWORD size  
);  
  
void Func3(_Out_writes_(size) PSTR pb,   
    DWORD size  
);  
  
```  
  
## <a name="out-pstr"></a>_Out\_ PSTR  
 Die Verwendung von `_Out_ PSTR` fast immer falsch ist. Dies wird als ein Ausgabeparameter, der auf einen Zeichenpuffer zeigt interpretiert, und NULL-terminiert ist.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Eine Anmerkung wie `_In_ PCSTR` häufige und sinnvolle ist. Das Objekt zeigt auf eine Eingabezeichenfolge, die NULL-Terminierung aufweist, da die Vorbedingung der `_In_` ermöglicht die Erkennung einer NULL-terminierte Zeichenfolge.  
  
## <a name="in-wchar-p"></a>_In\_ WCHAR * p  
 `_In_ WCHAR* p`besagt, dass es ein Eingabezeiger ist `p` , verweist auf ein Zeichen. Dies ist jedoch in den meisten Fällen möglicherweise nicht der Spezifikation, die vorgesehen ist. Stattdessen wahrscheinlich beabsichtigt ist die Angabe von einer NULL endendes Array vorhanden ist. Verwenden Sie zu diesem Zweck `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 Es ist üblich, die korrekte Angabe von NULL-Terminierung fehlt. Verwenden Sie die entsprechende `STR` Version, um den Typ zu ersetzen, wie im folgenden Beispiel gezeigt.  
  
```cpp  
  
// Incorrect  
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
// Correct  
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
```  
  
## <a name="outrange"></a>_Out_range\_  
 Wenn der Parameter ein Zeiger ist und den Bereich des Werts des Elements auszudrücken, die den Zeiger zu verwendende gezeigt wird `_Deref_out_range_` anstelle von `_Out_range_`. Im folgenden Beispiel des Bereichs von * PcbFilled ausgedrückt wird, nicht PcbFilled.  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Out_range_(0, cbSize) DWORD *pcbFilled  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled   
);  
  
```  
  
 `_Deref_out_range_(0, cbSize)`ist nicht zwingend erforderlich, für einige Tools, da es von abgeleitet werden, kann `_Out_writes_to_(cbSize,*pcbFilled)`, aber der Vollständigkeit halber hier angezeigt.  
  
## <a name="wrong-context-in-when"></a>Falscher Kontext in _vorlagenformular beim\_  
 Eine andere häufiger Fehler ist nach der state-Evaluierung für Vorbedingungen verwenden. Im folgenden Beispiel `_Requires_lock_held_` eine solche Vorbedingung ist.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 Der Ausdruck `result` bezieht sich auf ein nach dem Status-Wert, der vor Status nicht verfügbar ist.  
  
## <a name="true-in-success"></a>"True" in _Success\_  
 Wenn die Funktion erfolgreich ausgeführt wird, wenn der Rückgabewert ungleich NULL ist, verwenden Sie `return != 0` als erfolgsbedingung anstelle von `return == TRUE`. Nonzero bedeutet nicht unbedingt Äquivalenz mit dem Istwert, die der Compiler für bereitstellt `TRUE`. Der Parameter für `_Success_` ist ein Ausdruck, und die folgenden Ausdrücke werden als gleichwertig ausgewertet: `return != 0`, `return != false`, `return != FALSE`, und `return` ohne Parameter oder Vergleiche.  
  
```cpp  
  
// Incorrect  
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
// Correct  
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
```  
  
## <a name="reference-variable"></a>Verweisvariable  
 Für eine Verweisvariable die Vorgängerversion von SAL impliziten Zeiger als Anmerkung Ziel verwendet und das Hinzufügen der erforderlichen eine `__deref` mit Anmerkungen, die an eine Verweisvariable angefügt. Diese Version verwendet das Objekt selbst und erfordert keine zusätzlichen `_Deref_`.  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
```  
  
## <a name="annotations-on-return-values"></a>Anmerkungen zu Rückgabewerten  
 Das folgende Beispiel zeigt ein häufig auftretendes Problem im Rückgabewert Anmerkungen.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 In diesem Beispiel `_Out_opt_` besagt, dass der Zeiger NULL als Teil der Vorbedingung möglicherweise. Vorbedingungen können jedoch nicht auf den Rückgabewert angewendet werden. In diesem Fall die richtige Anmerkung ist `_Ret_maybenull_`.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)
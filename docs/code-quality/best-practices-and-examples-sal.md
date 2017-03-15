---
title: "Empfohlene Vorgehensweisen und Beispiele (SAL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Empfohlene Vorgehensweisen und Beispiele (SAL)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Folgenden einige Methoden, die die meisten aus \(Source Code Annotation Language SAL\) abzurufen und einige allgemeine Probleme zu vermeiden.  
  
## \_In\_  
 Wenn die Funktion auf Element schreiben soll, verwenden Sie `_Inout_` anstelle von `_In_`.  Dies ist bei automatisierten Konvertierung aus älteren Makros zu SAL besonders relevant.  Vor SAL haben viele Programmierer Makros als KommentarMakros, die `IN`, `OUT`, `IN_OUT` oder Varianten dieser Namen benannt wurden.  Auch wenn empfohlen wird, diese Makros zu SAL konvertieren, drängen wir Sie auch, achtzugeben, wenn Sie sie umwandeln, da der Code geändert wurde, seitdem der ursprüngliche Prototyp geschrieben wurde und das alte Makro möglicherweise nicht mehr reflektierte, welchem Zweck.  Seien Sie besonders zum `OPTIONAL` Kommentarmakro, da oftmals falsch\-für Beispiel platziert wird, auf die falsche Seite eines Kommas acht.  
  
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
  
## \_opt\_  
 Wenn der Aufrufer nicht die Übergabe in einem NULL\-Zeiger zulässig ist, verwenden Sie `_In_` oder `_Out_` anstelle von `_In_opt_` oder `_Out_opt_`.  Dies gilt sogar eine Funktion auf, die die Parameter überprüft und ein Fehler zurückgegeben wird, wenn er NULL ist, wenn nicht sein sollte.  Obwohl, eine Funktionsüberprüfung spornt, sein Parameter für unerwartete NULL und Rückgabe ordnungsgemäß gutes defensives Codierungsüblich ist, bedeutet dies nicht, dass die Parameteranmerkung von einem optionalen Typ \(\_Xxx\_opt\_\) sein kann.  
  
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
  
## \_Pre\_defensive\_ und \_Post\_defensive\_  
 Wenn eine Funktion in einer Vertrauenswürdigkeitsgrenze wird, wird empfohlen, die `_Pre_defensive_` verwenden Anmerkung.  Der "defensive" Modifizierer ändern sich bestimmte Anmerkungen, um anzugeben, dass, zum Zeitpunkt des Aufrufs, die Schnittstelle soll exklusiv ausgecheckt werden weitergegeben werden könnten, in Implementierungstext sie davon ausgehen sollte, dass möglicherweise falsche Parameter.  In diesem Fall wird `_In_ _Pre_defensive_` an einer Vertrauenswürdigkeitsgrenze bevorzugt, um anzugeben, dass, obwohl ein Aufrufer einen Fehler abruft, wenn er versucht, NULL zu übergeben, der Funktionsrumpf, als ob der Parameter möglicherweise NULL ist, und jeder Versuch, die Zeiger ohne erste Überprüfung zu dereferenzierende analysiert wird, die es für NULL gekennzeichnet ist.  Eine `_Post_defensive_` \- Anmerkung ist auch, die in den Rückrufen verfügbar, in denen die vertrauenswürdige Seite angenommen wird, dass der Aufrufer werden und der nicht vertrauenswürdige Code der aufgerufene Code ist.  
  
## \_Out\_writes\_  
 Im folgenden Beispiel wird eine häufige Verwendung von `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 Die Anmerkung `_Out_writes_` gibt an, dass Sie den Puffer haben.  Sie können `cb` Bytes zuordnen, wenn das erste Byte auf dem initialisiert ist.  Die Anmerkung ist nicht unbedingt falsch und ist es hilfreich, die zugehörige Größe auszudrücken.  Es wird nicht mit, wie viele Elemente durch die Funktion initialisiert werden.  
  
 Die wird des folgenden Beispiels richtige drei Möglichkeiten, die genaue Größe des initialisierten Teils des Puffers vollständig angeben.  
  
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
  
## \_Out\_ PSTR  
 Die Verwendung von `_Out_ PSTR` ist fast immer ungültig.  Dies wird als interpretiert, eines Ausgabeparameters verfügen, der auf einen Zeichenpuffer und es auf null endende ist.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Eine Anmerkung wie `_In_ PCSTR` und ist häufig nützlich.  Sie zeigt auf eine Eingabezeichenfolge, die Beendigung UNGÜLTIGE hat, da die Vorbedingung von `_In_` die Erkennung einer auf NULL endende Zeichenfolge zulässig.  
  
## \_In\_ WCHAR\* p  
 `_In_ WCHAR* p` besagt, dass ein Eingabezeiger `p` gibt, der auf einem Zeichen zeigt.  In den meisten Fällen ist dies wahrscheinlich nicht der Funktionsspezifikation, die bestimmt wird.  Stattdessen was wahrscheinlich vorgesehen ist, ist die Spezifikation eines auf NULL endende Arrays; um das zu erreichen, verwenden Sie `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 Die richtige Spezifikation der NULL\- Ende von fehlen ist üblich.  Mit der entsprechenden Version `STR`, um den Typ, wie im folgenden Beispiel dargestellt zu ersetzen.  
  
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
  
## \_Out\_range\_  
 Wenn der Parameter ein Zeiger ist und Sie den Bereich des Werts des Elements angeben möchten, das auf der Zeiger angezeigt wird, verwenden Sie `_Deref_out_range_` anstelle von `_Out_range_`.  Im folgenden Beispiel wird der Bereich von \*pcbFilled ausgedrückt, pcbFilled nicht.  
  
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
  
 `_Deref_out_range_(0, cbSize)` ist nicht zwingend für einige Tools müssen, da es von `_Out_writes_to_(cbSize,*pcbFilled)` abgeleitet werden kann, jedoch wird der Vollständigkeit halber hier angezeigt.  
  
## Falscher Kontext in \_When\_  
 Ein weiterer häufiger Fehler ist, BeitragZustandsauswertung für Vorbedingungen zu verwenden.  Im folgenden Beispiel ist `_Requires_lock_held_` eine Vorbedingung.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 Der Ausdruck `result` ist ein BeitragZustandswert an, der nicht im VorZustand verfügbar ist.  
  
## TRUE in \_Success\_  
 Wenn die Funktion erfolgreich ist, wenn der Rückgabewert ungleich 0 ist, verwenden Sie `return != 0` als Erfolgszustand anstelle von `return == TRUE`.  Wert ungleich 0 \(null\) bedeutet nicht unbedingt Äquivalenz in den tatsächlichen Wert, den der Compiler für `TRUE` bereitstellt.  Der Parameter für `_Success_` ist ein Ausdruck, und die folgenden Ausdrücke werden als Entsprechung ausgewertet: `return != 0`, `return != false`, `return != FALSE` und `return` ohne Parameter oder Vergleiche.  
  
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
  
## Verweisvariable  
 Für eine Verweisvariable verwendet die frühere Version des SALZES den impliziten Zeiger als das Anmerkungsziel und erforderte Hinzufügung von `__deref` in den Anmerkungen, die an eine Verweisvariable angefügt wurde.  Diese Version verwendet das Objekt selbst und erfordert keine zusätzliche `_Deref_`.  
  
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
  
## Anmerkungen zu Rückgabewerten  
 Im folgenden Beispiel wird ein häufiges Problem bewerten als Ausgleich Anmerkungen an.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 In diesem Beispiel lautet `_Out_opt_`, ob der Zeiger als Teil der Vorbedingung NULL ist.  Sie können Vorbedingungen nicht auf den Rückgabewert angewendet werden.  In diesem Fall ist die richtige Anmerkung `_Ret_maybenull_`.  
  
## Siehe auch  
 [Verwenden von SAL\-Anmerkungen zum Reduzieren von C\/C\+\+\-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)
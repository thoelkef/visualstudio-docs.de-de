---
title: Empfohlene Vorgehensweisen und Beispiele (SAL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 14
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5abb716bd562b6bd82b430f6b94251153a9abbe3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934703"
---
# <a name="best-practices-and-examples-sal"></a>Empfohlene Vorgehensweisen und Beispiele (SAL)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hier sind einige Möglichkeiten, um die am häufigsten aus der Source Code Annotation Language (SAL) zu erhalten und einige der häufigsten Probleme zu vermeiden.  
  
## <a name="in"></a>\_In\_
 Wenn die Funktion zum Schreiben in das Element soll, verwenden Sie `_Inout_` anstelle von `_In_`. Dies ist besonders wichtig, im Fall von automatischen Konvertieren von älteren Makros zu SAL. Vor dem SAL, zahlreiche Programmierer verwendeten Makros als Kommentare, Makros, die mit dem Namen wurden `IN`, `OUT`, `IN_OUT`, oder Varianten dieser Namen. Jedoch wir empfehlen, diese Makros in SAL zu konvertieren, dringend auch darauf achten, wenn Sie sie konvertieren, da der Code möglicherweise geändert wurden, da der ursprüngliche Prototyp geschrieben wurde und das alte-Makro möglicherweise nicht mehr widerspiegeln, was der Code bewirkt. Seien Sie besonders die `OPTIONAL` Makro kommentieren, da sie häufig falsch platziert wird – z. B. auf die Seite von einem Komma.  
  
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
  
## <a name="opt"></a>\_opt\_  
 Wenn der Aufrufer nicht zulässig ist, ein null-Zeiger übergeben, verwenden Sie `_In_` oder `_Out_` anstelle von `_In_opt_` oder `_Out_opt_`. Dies gilt auch für eine Funktion, die überprüft die Parameter und gibt einen Fehler zurück, wenn er NULL ist, wenn es nicht sein sollten. Zwar müssen eine Funktion als Parameter für den unerwarteten NULL zu prüfen und ordnungsgemäß zurückzugeben defensive Programmierung bewährt, dies bedeutet nicht, dass die parameteranmerkung ein optionaler Typ aufweisen kann (\_*Xxx*_opt\_).  
  
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
  
## <a name="predefensive-and-postdefensive"></a>\_Pre_defensive\_ und \_Post_defensive\_  
 Wenn eine Funktion eine Vertrauensgrenze angezeigt wird, es wird empfohlen, die Sie verwenden die `_Pre_defensive_` Anmerkung.  Der Modifizierer "defensive" ändert bestimmte Anmerkungen, die zum Zeitpunkt des Aufrufs angeben, die Schnittstelle sollte unbedingt aktiviert sein, aber in den implementierungstext sollten davon ausgehen, dass falsche Parameter übergeben werden können. In diesem Fall `_In_ _Pre_defensive_` wird an eine Vertrauensgrenze, um anzugeben, dass obwohl ein Aufrufer eine Fehlermeldung erhalten wird, wenn versucht wird, übergeben Sie NULL, Hauptteil der Funktion analysiert werden sollen, als ob der Parameter NULL ist, und jeder Versuch, den Zeiger, ohne zuerst aufheben verweisen möglicherweise bevorzugt Überprüfen es auf NULL werden gekennzeichnet.  Ein `_Post_defensive_` -Anmerkung ist ebenfalls verfügbar, für die Verwendung in Rückrufen, in dem vertrauenswürdige Partei wird davon ausgegangen, dass der Aufrufer sein und der nicht vertrauenswürdige Code wird der aufgerufenen Code.  
  
## <a name="outwrites"></a>\_Out_writes\_  
 Das folgende Beispiel zeigt eine allgemeine unsachgemäße Verwendung des `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 Die Anmerkung `_Out_writes_` gibt an, dass Sie einen Puffer haben. Sie verfügt über `cb` Bytes zugewiesen, mit dem ersten Byte, die beim Beenden initialisiert. Diese Anmerkung ist nicht unbedingt falsch, und es ist hilfreich, die die zugeordnete Größe express. Jedoch ist er nicht erkennen, wie viele Elemente, die von der Funktion initialisiert werden.  
  
 Das nächste Beispiel zeigt drei richtige Möglichkeiten, um die genaue Größe des Teils der Puffer initialisiert vollständig anzugeben.  
  
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
  
## <a name="out-pstr"></a>\_Out\_ PSTR  
 Die Verwendung von `_Out_ PSTR` ist fast immer falsch. Dies wird als einen Ausgabeparameter, der auf einen Zeichenpuffer zeigt interpretiert, und NULL-terminiert werden kann.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Eine Anmerkung wie `_In_ PCSTR` ist allgemeine und nützlich. Er zeigt auf eine Eingabezeichenfolge, die NULL-Terminierung verfügt, da die Vorbedingung der `_In_` ermöglicht die Erkennung einer NULL-terminierte Zeichenfolge.  
  
## <a name="in-wchar-p"></a>\_In\_ WCHAR * p  
 `_In_ WCHAR* p` besagt, dass es ein Eingabe Zeiger ist `p` , um ein Zeichen zeigt. Dies ist jedoch in den meisten Fällen wahrscheinlich nicht der Spezifikation, die vorgesehen ist. Stattdessen wahrscheinlich beabsichtigt ist die Angabe einer NULL endendes Array vorhanden ist. Verwenden Sie zu diesem Zweck `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 Es ist üblich, die richtige Angabe von NULL-Terminierung fehlt. Verwenden Sie die entsprechende `STR` Version, um den Typ zu ersetzen, wie im folgenden Beispiel gezeigt.  
  
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
  
## <a name="outrange"></a>\_Out_range\_  
 Wenn der Parameter ein Zeiger ist und Sie möchten, das Spektrum der Wert der Elements auszudrücken, die für die Verwendung durch die Zeiger gezeigt wird `_Deref_out_range_` anstelle von `_Out_range_`. Im folgenden Beispiel, das Spektrum * PcbFilled ausgedrückt wird, nicht PcbFilled.  
  
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
  
 `_Deref_out_range_(0, cbSize)` ist nicht zwingend erforderlich, für einige Tools, da es von abgeleitet werden, kann `_Out_writes_to_(cbSize,*pcbFilled)`, wird aber aus Gründen der Vollständigkeit hier angezeigt.  
  
## <a name="wrong-context-in-when"></a>Falscher Kontext in \_bei\_  
 Ein häufiger Fehler ist, nach dem zustandsauswertung für Vorbedingungen zu verwenden. Im folgenden Beispiel `_Requires_lock_held_` ist eine Vorbedingung.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 Der Ausdruck `result` bezieht sich auf ein nach dem Status-Wert, der vor Status nicht verfügbar ist.  
  
## <a name="true-in-success"></a>In "true" \_Erfolg\_  
 Wenn die Funktion erfolgreich ist, wenn der Rückgabewert ungleich NULL ist, verwenden Sie `return != 0` als erfolgsbedingung ein anstelle von `return == TRUE`. Nonzero bedeutet nicht unbedingt Übereinstimmung mit den tatsächlichen Wert, der der Compiler für bereitstellt `TRUE`. Der Parameter für `_Success_` ist ein Ausdruck, und die folgenden Ausdrücke werden als gleichwertig ausgewertet: `return != 0`, `return != false`, `return != FALSE`, und `return` ohne Parameter oder vergleichen.  
  
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
 Für eine Reference-Variable, die vorherige Version von SAL den impliziten Zeiger als das anmerkungsziel verwendet und erforderlich, das Hinzufügen einer `__deref` , Anmerkungen, die an eine Variable als Verweis angefügt. Diese Version verwendet das Objekt selbst und erfordert keine zusätzliche `_Deref_`.  
  
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
 Das folgende Beispiel zeigt ein typisches Problem im Rückgabewert Anmerkungen.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 In diesem Beispiel `_Out_opt_` besagt, dass der Zeiger NULL als Teil der Vorbedingung sein kann. Vorbedingungen können jedoch auf den Rückgabewert angewendet werden. In diesem Fall die richtige Anmerkung ist `_Ret_maybenull_`.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen von Kommentaren Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)




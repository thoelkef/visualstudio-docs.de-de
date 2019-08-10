---
title: Empfohlene Vorgehensweisen und Beispiele (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 478efc77bd1fb14f6241e026cfe280355a90746a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919447"
---
# <a name="best-practices-and-examples-sal"></a>Empfohlene Vorgehensweisen und Beispiele (SAL)
Im folgenden finden Sie einige Möglichkeiten, die Quell Code Anmerkung (Source Code Annotation Language, SAL) optimal zu nutzen und einige häufige Probleme zu vermeiden.

## <a name="_in_"></a>\_In\_

Wenn die Funktion in das-Element schreiben soll, verwenden `_Inout_` Sie anstelle von. `_In_` Dies ist insbesondere bei der automatisierten Konvertierung von älteren Makros in SAL von Bedeutung. Vor SAL verwendeten viele Programmierer Makros als Kommentare – Makros `IN`mit den Namen, `OUT`, `IN_OUT`oder Varianten dieser Namen. Es wird empfohlen, dass Sie diese Makros in SAL konvertieren, aber wir sollten auch darauf achten, dass Sie bei der Konvertierung sorgfältig vorgehen, da der Code möglicherweise geändert wurde, seit der ursprüngliche Prototyp geschrieben wurde, und das alte Makro nicht mehr die Funktionsweise des Codes widerspiegelt. Achten Sie besonders auf das `OPTIONAL` Kommentar Makro, weil es häufig falsch platziert wird – z. b. auf der falschen Seite eines Kommas.

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

## <a name="_opt_"></a>\_opt\_

Wenn der Aufrufer nicht in der Übergabe eines NULL-Zeigers `_In_` zulässig `_Out_` ist, verwenden `_Out_opt_`Sie oder anstelle von `_In_opt_` oder. Dies gilt auch für eine Funktion, die ihre Parameter überprüft und einen Fehler zurückgibt, wenn Sie NULL ist, wenn Sie nicht sein sollte. Obwohl eine Funktion den Parameter auf unerwartete NULL überprüft und ordnungsgemäß zurückgegeben wird, handelt es sich um eine gute defensive Codierungs Praxis. Dies bedeutet nicht, dass die Parameter Anmerkung einen optionalen`_*Xxx*_opt_`Typ () aufweisen kann.

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

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Vor\_- und\_nachder\_Defensive\_\_

Wenn eine Funktion an einer Vertrauens Grenze angezeigt wird, empfiehlt es sich, die `_Pre_defensive_` -Anmerkung zu verwenden.  Durch den "defensive"-Modifizierer werden bestimmte Anmerkungen geändert, um anzugeben, dass die Schnittstelle zum Zeitpunkt des Aufrufes strikt geprüft werden soll. im Implementierungs Text sollte jedoch davon ausgegangen werden, dass falsche Parameter passieren können. In diesem Fall `_In_ _Pre_defensive_` wird an einer Vertrauensstellungs Grenze bevorzugt, um anzugeben, dass ein Aufrufer zwar einen Fehler erhält, wenn er versucht, NULL zu übergeben, der Funktions Rumpf jedoch analysiert wird, als ob der Parameter NULL sein kann, und alle Versuche, auf den Zeiger ohne erstes zu verweisen. die Überprüfung auf NULL wird gekennzeichnet.  Es `_Post_defensive_` ist auch eine Anmerkung verfügbar, die für Rückrufe verwendet werden kann, bei denen davon ausgegangen wird, dass die vertrauenswürdige Partei der Aufrufer ist und der nicht vertrauenswürdige Code der aufgerufene Code ist.

## <a name="_out_writes_"></a>\_Out\_-Schreibvorgänge\_

Das folgende Beispiel veranschaulicht einen allgemeinen Missbrauch von `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

`_Out_writes_` Die-Anmerkung gibt an, dass ein Puffer vorhanden ist. Es sind zugeordnete Bytes, wobei das erste Byte beim Beenden initialisiert wird. `cb` Diese Anmerkung ist nicht streng falsch, und es ist hilfreich, die zugeordnete Größe auszudrücken. Sie gibt jedoch nicht an, wie viele Elemente von der Funktion initialisiert werden.

Das nächste Beispiel zeigt drei richtige Möglichkeiten, um die genaue Größe des initialisierten Teils des Puffers vollständig anzugeben.

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

## <a name="_out_-pstr"></a>\_Out\_ -Pstr

Die Verwendung von `_Out_ PSTR` ist fast immer falsch. Dies wird als vorhanden sein eines Output-Parameters interpretiert, der auf einen Zeichen Puffer zeigt und NULL-terminiert ist.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Eine Anmerkung wie `_In_ PCSTR` ist häufig und hilfreich. Er verweist auf eine Eingabe Zeichenfolge, die NULL-Beendigung hat `_In_` , da die Vorbedingung von das Erkennen einer null-terminierten Zeichenfolge zulässt.

## <a name="_in_-wchar-p"></a>\_In\_ WCHAR * p

`_In_ WCHAR* p`Gibt an, dass es einen Eingabe `p` Zeiger gibt, der auf ein Zeichen zeigt. In den meisten Fällen ist dies jedoch wahrscheinlich nicht die Spezifikation, die vorgesehen ist. Stattdessen ist die Angabe eines null-terminierten Arrays wahrscheinlich beabsichtigt. verwenden `_In_ PWSTR`Sie hierzu.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Die richtige Angabe der NULL-Beendigung fehlt häufig. Verwenden Sie die `STR` entsprechende Version, um den Typ zu ersetzen, wie im folgenden Beispiel gezeigt.

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

## <a name="_out_range_"></a>\_Bereich\_außerhalb\_

Wenn der-Parameter ein-Zeiger ist und Sie den Bereich des Werts des Elements, auf das der-Zeiger zeigt, ausdrücken möchten, verwenden `_Deref_out_range_` Sie anstelle `_Out_range_`von. Im folgenden Beispiel wird der Bereich von * pcbfill ausgedrückt, nicht pcbfill.

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

`_Deref_out_range_(0, cbSize)`ist für einige Tools nicht unbedingt erforderlich, da Sie von abgeleitet werden kann `_Out_writes_to_(cbSize,*pcbFilled)`, Sie wird jedoch aus Gründen der Vollständigkeit hier angezeigt.

## <a name="wrong-context-in-_when_"></a>Falscher Kontext in \_when\_

Ein weiterer häufiger Fehler ist die Verwendung der Post-State-Auswertung für Vorbedingungen. Im folgenden Beispiel `_Requires_lock_held_` ist eine Vorbedingung.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

Der Ausdruck `result` verweist auf einen Wert nach dem Zustand, der im Zustand vor dem Zustand nicht verfügbar ist.

## <a name="true-in-_success_"></a>TRUE in \_Erfolg\_

Wenn die Funktion erfolgreich ist, wenn der Rückgabewert ungleich 0 ( `return != 0` null) ist, verwenden Sie `return == TRUE`als Erfolgs Bedingung anstelle von. Ungleich NULL bedeutet nicht notwendigerweise, dass die Entsprechungen zu dem tatsächlichen Wert, den `TRUE`der Compiler bereitstellt, übereinstimmt. Der-Parameter `_Success_` für ist ein Ausdruck, und die folgenden Ausdrücke werden als Äquivalent ausgewertet `return != 0`: `return != false`, `return != FALSE`, und `return` ohne Parameter oder Vergleiche.

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

## <a name="reference-variable"></a>Verweis Variable

Bei einer Verweis Variablen wurde in der vorherigen Version von Sal der implizite Zeiger als Anmerkung verwendet, und das Hinzufügen von `__deref` zu Anmerkungen, die an eine Verweis Variable angefügt wurden, ist erforderlich. Diese Version verwendet das-Objekt selbst und erfordert nicht das zusätzliche `_Deref_`.

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

## <a name="annotations-on-return-values"></a>Anmerkungen zu Rückgabe Werten

Das folgende Beispiel zeigt ein häufiges Problem in den Anmerkungen zu Rückgabe Werten.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

In diesem Beispiel besagt `_Out_opt_` , dass der Zeiger im Rahmen der Vorbedingung Null sein kann. Vorbedingungen können jedoch nicht auf den Rückgabewert angewendet werden. In diesem Fall ist `_Ret_maybenull_`die korrekte Anmerkung.

## <a name="see-also"></a>Siehe auch

[Verwenden von Sal-Anmerkungen zum Reduzieren vonC++ C/Code-Fehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
[verstehen von Sal](../code-quality/understanding-sal.md)
[kommentieren von Funktionsparametern und Rückgabe Werten](../code-quality/annotating-function-parameters-and-return-values.md)
Hinzufügen von[Anmerkungen zum Funktionsverhalten](../code-quality/annotating-function-behavior.md) 
Hinzufügen einer [Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)
[kommentieren von Sperr Verhalten](../code-quality/annotating-locking-behavior.md)
[angeben, wann und wo eine Anmerkung intrinsische](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[Funktionen](../code-quality/intrinsic-functions.md) anwendet
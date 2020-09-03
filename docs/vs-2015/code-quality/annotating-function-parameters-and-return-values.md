---
title: Kommentieren von Funktionsparametern und Rückgabe Werten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 71854388f3fb1c5eaea7d40ed2757af9cecacf1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543805"
---
# <a name="annotating-function-parameters-and-return-values"></a>Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Artikel werden typische Verwendungsmöglichkeiten von Anmerkungen für einfache Funktionsparameter – skalare und Zeiger auf Strukturen und Klassen – und die meisten Puffer Typen beschrieben.  Dieser Artikel zeigt auch gängige Verwendungs Muster für Anmerkungen. Weitere Anmerkungen, die sich auf Funktionen beziehen, finden Sie unter [kommentieren von Funktionsverhalten](../code-quality/annotating-function-behavior.md) .  
  
## <a name="pointer-parameters"></a>Zeigerparameter  
 Wenn für die Anmerkungen in der folgenden Tabelle ein Zeiger Parameter mit Anmerkungen versehen wird, meldet der Analyzer einen Fehler, wenn der Zeiger NULL ist.  Dies gilt für Zeiger und für jedes Datenelement, auf das verwiesen wird.  
  
 **Anmerkungen und Beschreibungen**  
  
- `_In_`  
  
     Kommentiert Eingabe Parametern, bei denen es sich um skalare, Strukturen, Zeiger auf Strukturen und ähnliches handelt.  Kann explizit auf einfachen skalaren verwendet werden.  Der-Parameter muss im Voraus State gültig sein und wird nicht geändert.  
  
- `_Out_`  
  
     Kommentiert Ausgabeparameter, bei denen es sich um skalare, Strukturen, Zeiger auf Strukturen und ähnliches handelt.  Wenden Sie diese nicht auf ein Objekt an, das keinen Wert zurückgeben kann, z. –. ein Skalar, der als Wert übergangen wird.  Der-Parameter muss im Voraus State nicht gültig sein, muss jedoch im Post-Status gültig sein.  
  
- `_Inout_`  
  
     Kommentiert einen Parameter, der von der-Funktion geändert wird.  Er muss sowohl im Zustand vor als auch nach dem Status gültig sein, es wird jedoch davon ausgegangen, dass er vor und nach dem-Befehl über unterschiedliche Werte verfügt. Muss auf einen änderbaren Wert angewendet werden.  
  
- `_In_z_`  
  
     Ein Zeiger auf eine auf NULL endende Zeichenfolge, die als Eingabe verwendet wird.  Die Zeichenfolge muss im Voraus State gültig sein.  Varianten von `PSTR` , die bereits über die richtigen Anmerkungen verfügen, werden bevorzugt.  
  
- `_Inout_z_`  
  
     Ein Zeiger auf ein mit Null endendes Zeichen Array, das geändert wird.  Sie muss vor und nach dem-Befehl gültig sein, aber es wird davon ausgegangen, dass sich der Wert geändert hat.  Der NULL-Terminator kann verschoben werden, aber nur die Elemente bis zum ursprünglichen null-Terminator können aufgerufen werden.  
  
- `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     Ein Zeiger auf ein Array, das von der Funktion gelesen wird.  Das Array weist Größen `s` Elemente auf, die alle gültig sein müssen.  
  
     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie dies nur, wenn die Größe nicht als Elemente ausgedrückt werden kann.  Beispielsweise würden Zeichen folgen `char` die `_bytes_` Variante nur dann verwenden, wenn eine ähnliche Funktion, die verwendet, `wchar_t` wäre.  
  
- `_In_reads_z_(s)`  
  
     Ein Zeiger auf ein Array, das NULL-terminierte und eine bekannte Größe aufweist. Die Elemente bis zum NULL-Terminator – oder, `s` Wenn kein NULL-Terminator vorhanden ist – müssen im Zustand "vorab" gültig sein.  Wenn die Größe in Bytes bekannt ist, Skalieren Sie `s` nach der Elementgröße.  
  
- `_In_reads_or_z_(s)`  
  
     Ein Zeiger auf ein Array, das NULL-terminierte oder eine bekannte Größe hat, oder beides. Die Elemente bis zum NULL-Terminator – oder, `s` Wenn kein NULL-Terminator vorhanden ist – müssen im Zustand "vorab" gültig sein.  Wenn die Größe in Bytes bekannt ist, Skalieren Sie `s` nach der Elementgröße.  (Wird für die `strn` Familie verwendet.)  
  
- `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Ein Zeiger auf ein Array von- `s` Elementen (bzw. Bytes), die von der-Funktion geschrieben werden.  Die Array Elemente müssen nicht im Voraus State gültig sein, und die Anzahl der Elemente, die im Post-State gültig sind, ist nicht angegeben.  Wenn Anmerkungen zum Parametertyp vorhanden sind, werden Sie im Post-State angewendet. Betrachten Sie hierzu den folgenden Beispielcode:  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     In diesem Beispiel stellt der Aufrufer einen Puffer von `size` Elementen für bereit `p1` .  `MyStringCopy` macht einige dieser Elemente gültig. Noch wichtiger ist, `_Null_terminated_` dass die Anmerkung in `PWSTR` bedeutet, dass `p1` im Post-State NULL-terminiert ist.  Auf diese Weise ist die Anzahl der gültigen Elemente immer noch klar definiert, aber eine bestimmte Element Anzahl ist nicht erforderlich.  
  
     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie dies nur, wenn die Größe nicht als Elemente ausgedrückt werden kann.  Beispielsweise würden Zeichen folgen `char` die `_bytes_` Variante nur dann verwenden, wenn eine ähnliche Funktion, die verwendet, `wchar_t` wäre.  
  
- `_Out_writes_z_(s)`  
  
     Ein Zeiger auf ein Array von- `s` Elementen.  Die Elemente müssen nicht im Voraus State gültig sein.  Im Post-Zustand müssen die Elemente, die durch das NULL-Abschluss Zeichen – das vorhanden sein müssen – gültig sein.  Wenn die Größe in Bytes bekannt ist, Skalieren Sie `s` nach der Elementgröße.  
  
- `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Ein Zeiger auf ein Array, das in der Funktion gelesen und geschrieben wird.  Es `s` hat Größen Elemente und ist im Zustand vor und nach dem Zustand gültig.  
  
     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie dies nur, wenn die Größe nicht als Elemente ausgedrückt werden kann.  Beispielsweise würden Zeichen folgen `char` die `_bytes_` Variante nur dann verwenden, wenn eine ähnliche Funktion, die verwendet, `wchar_t` wäre.  
  
- `_Inout_updates_z_(s)`  
  
     Ein Zeiger auf ein Array, das NULL-terminierte und eine bekannte Größe aufweist. Die Elemente, die durch das NULL-Abschluss Zeichen – die vorhanden sein müssen, müssen – sowohl im Zustand vor als auch nach dem Status gültig sein.  Es wird davon ausgegangen, dass sich der Wert im Post-State von dem Wert im Zustand "vor" unterscheidet. Dazu gehört auch der Speicherort des NULL-Terminator. Wenn die Größe in Bytes bekannt ist, Skalieren Sie `s` nach der Elementgröße.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Ein Zeiger auf ein Array von- `s` Elementen.  Die Elemente müssen nicht im Voraus State gültig sein.  Im Post-State müssen die Elemente bis zum `c` -th-Element gültig sein.  Wenn die Größe in Bytes bekannt ist, Skalieren Sie `s` und `c` nach der Elementgröße, oder verwenden Sie die `_bytes_` Variante, die wie folgt definiert ist:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Das heißt, dass jedes Element, das im Puffer bis zu `s` im Zustand "Pre" vorhanden ist, im Post-State gültig ist.  Beispiel:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Ein Zeiger auf ein Array, das von der Funktion gelesen und geschrieben wird.  Sie weist Größen `s` Elemente auf, die alle im Zustand vor dem Zustand gültig sein müssen, und die `c` Elemente müssen im Post-State gültig sein.  
  
     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie dies nur, wenn die Größe nicht als Elemente ausgedrückt werden kann.  Beispielsweise würden Zeichen folgen `char` die `_bytes_` Variante nur dann verwenden, wenn eine ähnliche Funktion, die verwendet, `wchar_t` wäre.  
  
- `_Inout_updates_z_(s)`  
  
     Ein Zeiger auf ein Array, das NULL-terminierte und eine bekannte Größe aufweist. Die Elemente, die durch das NULL-Abschluss Zeichen – die vorhanden sein müssen, müssen – sowohl im Zustand vor als auch nach dem Status gültig sein.  Es wird davon ausgegangen, dass sich der Wert im Post-State von dem Wert im Zustand "vor" unterscheidet. Dazu gehört auch der Speicherort des NULL-Terminator. Wenn die Größe in Bytes bekannt ist, Skalieren Sie `s` nach der Elementgröße.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Ein Zeiger auf ein Array von- `s` Elementen.  Die Elemente müssen nicht im Voraus State gültig sein.  Im Post-State müssen die Elemente bis zum `c` -th-Element gültig sein.  Wenn die Größe in Bytes bekannt ist, Skalieren Sie `s` und `c` nach der Elementgröße, oder verwenden Sie die `_bytes_` Variante, die wie folgt definiert ist:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Das heißt, dass jedes Element, das im Puffer bis zu `s` im Zustand "Pre" vorhanden ist, im Post-State gültig ist.  Beispiel:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Ein Zeiger auf ein Array, das von der Funktion gelesen und geschrieben wird.  Sie weist Größen `s` Elemente auf, die alle im Zustand vor dem Zustand gültig sein müssen, und die `c` Elemente müssen im Post-State gültig sein.  
  
     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie dies nur, wenn die Größe nicht als Elemente ausgedrückt werden kann.  Beispielsweise würden Zeichen folgen `char` die `_bytes_` Variante nur dann verwenden, wenn eine ähnliche Funktion, die verwendet, `wchar_t` wäre.  
  
- `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Ein Zeiger auf ein Array, das von der Funktion der Size-Elemente gelesen und geschrieben wird `s` . Definiert als äquivalent zu:  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     Das heißt, dass jedes Element, das im Puffer bis zu im Zustand "Pre" vorhanden `s` ist, im Zustand vor und nach dem Zustand gültig ist.  
  
     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie dies nur, wenn die Größe nicht als Elemente ausgedrückt werden kann.  Beispielsweise würden Zeichen folgen `char` die `_bytes_` Variante nur dann verwenden, wenn eine ähnliche Funktion, die verwendet, `wchar_t` wäre.  
  
- `_In_reads_to_ptr_(p)`  
  
     Ein Zeiger auf ein Array, für das der Ausdruck – (d. h `p` `_Curr_` `p` `_Curr_` . minus) durch den entsprechenden Sprachstandard definiert wird.  Die Elemente vor `p` müssen im Voraus State gültig sein.  
  
- `_In_reads_to_ptr_z_(p)`  
  
     Ein Zeiger auf ein mit Null endendes Array, für das der Ausdruck – (d. h `p` `_Curr_` `p` `_Curr_` . minus) durch den entsprechenden Sprachstandard definiert wird.  Die Elemente vor `p` müssen im Voraus State gültig sein.  
  
- `_Out_writes_to_ptr_(p)`  
  
     Ein Zeiger auf ein Array, für das der Ausdruck – (d. h `p` `_Curr_` `p` `_Curr_` . minus) durch den entsprechenden Sprachstandard definiert wird.  Die Elemente vor müssen `p` nicht im Voraus State gültig sein und müssen im Post-State gültig sein.  
  
- `_Out_writes_to_ptr_z_(p)`  
  
     Ein Zeiger auf ein mit Null endendes Array, für das der Ausdruck – (d. h `p` `_Curr_` `p` `_Curr_` . minus) durch den entsprechenden Sprachstandard definiert wird.  Die Elemente vor müssen `p` nicht im Voraus State gültig sein und müssen im Post-State gültig sein.  
  
## <a name="optional-pointer-parameters"></a>Optionale Zeigerparameter  
 Wenn eine Zeiger Parameter Anmerkung enthält `_opt_` , gibt Sie an, dass der Parameter möglicherweise NULL ist. Andernfalls führt die-Anmerkung dieselbe wie die Version aus, die nicht enthält `_opt_` . Im folgenden finden Sie eine Liste der `_opt_` Varianten der Zeiger Parameter Anmerkungen:  
  
`_In_opt_`, `_Out_opt_`, `_Inout_opt_`, `_In_opt_z_`, `_Inout_opt_z_`, `_In_reads_opt_`, `_In_reads_bytes_opt_`, `_In_reads_opt_z_`|`_Out_writes_opt_`, `_Out_writes_opt_z_`, `_Inout_updates_opt_`, `_Inout_updates_bytes_opt_`, `_Inout_updates_opt_z_`, `_Out_writes_to_opt_`, `_Out_writes_bytes_to_opt_`, `_Out_writes_all_opt_`, `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`, `_Inout_updates_bytes_to_opt_`, `_Inout_updates_all_opt_`, `_Inout_updates_bytes_all_opt_`, `_In_reads_to_ptr_opt_`, `_In_reads_to_ptr_opt_z_`, `_Out_writes_to_ptr_opt_`, `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Ausgabezeigerparameter  
 Ausgabe Zeiger Parameter erfordern eine besondere Schreibweise, um die NULL-Werte für den Parameter und den Punkt auf den Speicherort zu unterscheiden.  
  
 **Anmerkungen und Beschreibungen**  
  
- `_Outptr_`  
  
   Der Parameter darf nicht NULL sein, und im Post-State darf der Punkt-zu-Speicherort nicht NULL sein und muss gültig sein.  
  
- `_Outptr_opt_`  
  
   Der Parameter kann NULL sein, aber im Post-State darf der Punkt-zu-Speicherort nicht NULL sein und muss gültig sein.  
  
- `_Outptr_result_maybenull_`  
  
   Der-Parameter darf nicht NULL sein, und im Post-State kann der Punkt-zu-Standort den Wert NULL haben.  
  
- `_Outptr_opt_result_maybenull_`  
  
   Der-Parameter kann NULL sein, und im Post-State kann der Punkt-zu-Standort den Wert NULL haben.  
  
  In der folgenden Tabelle werden zusätzliche Teil Zeichenfolgen in den Namen der Anmerkung eingefügt, um die Bedeutung der Anmerkung weiter zu qualifizieren.  Die verschiedenen Teil Zeichenfolgen sind `_z` , `_COM_` , `_buffer_` , `_bytebuffer_` und `_to_` .  
  
> [!IMPORTANT]
> Wenn die Schnittstelle, die Sie kommentieren, com ist, verwenden Sie das com-Formular dieser Anmerkungen. Verwenden Sie die com-Anmerkungen nicht mit anderen typschnittstellen.  
  
 **Anmerkungen und Beschreibungen**  
  
- `_Outptr_result_z_`  
  
   `_Outptr_opt_result_z_`  
  
   `_Outptr_result_maybenull_z_`  
  
   `_Ouptr_opt_result_maybenull_z_`  
  
   Der zurückgegebene Zeiger verfügt über die-Anmerkung `_Null_terminated_` .  
  
- `_COM_Outptr_`  
  
   `_COM_Outptr_opt_`  
  
   `_COM_Outptr_result_maybenull_`  
  
   `_COM_Outptr_opt_result_maybenull_`  
  
   Der zurückgegebene Zeiger hat eine com-Semantik und führt daher eine `_On_failure_` nach Bedingung aus, dass der zurückgegebene Zeiger NULL ist.  
  
- `_Outptr_result_buffer_(s)`  
  
   `_Outptr_result_bytebuffer_(s)`  
  
   `_Outptr_opt_result_buffer_(s)`  
  
   `_Outptr_opt_result_bytebuffer_(s)`  
  
   Der zurückgegebene Zeiger verweist auf einen gültigen Puffer der Größen `s` Elemente oder Bytes.  
  
- `_Outptr_result_buffer_to_(s, c)`  
  
   `_Outptr_result_bytebuffer_to_(s, c)`  
  
   `_Outptr_opt_result_buffer_to_(s,c)`  
  
   `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
   Der zurückgegebene Zeiger zeigt auf einen Puffer der Größen `s` Elemente oder bytes, von denen der erste `c` gültig ist.  
  
  Bestimmte Schnittstellen Konventionen setzen voraus, dass Ausgabeparameter bei einem Fehler NULL sind.  Mit Ausnahme des expliziten com-Codes werden die Formulare in der folgenden Tabelle bevorzugt.  Verwenden Sie für com-Code die entsprechenden com-Formulare, die im vorherigen Abschnitt aufgelistet sind.  
  
  **Anmerkungen und Beschreibungen**  
  
- `_Result_nullonfailure_`  
  
   Ändert andere Anmerkungen. Das Ergebnis wird auf NULL festgelegt, wenn die Funktion fehlschlägt.  
  
- `_Result_zeroonfailure_`  
  
   Ändert andere Anmerkungen. Das Ergebnis wird auf 0 festgelegt, wenn die Funktion fehlschlägt.  
  
- `_Outptr_result_nullonfailure_`  
  
   Der zurückgegebene Zeiger zeigt auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder NULL, wenn die Funktion fehlschlägt. Diese Anmerkung gilt für einen nicht optionalen Parameter.  
  
- `_Outptr_opt_result_nullonfailure_`  
  
   Der zurückgegebene Zeiger zeigt auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder NULL, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen optionalen Parameter.  
  
- `_Outref_result_nullonfailure_`  
  
   Der zurückgegebene Zeiger zeigt auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder NULL, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen Verweis Parameter.  
  
## <a name="output-reference-parameters"></a>Ausgabeverweisparameter  
 Der Verweis Parameter wird häufig für Ausgabeparameter verwendet.  Für einfache Ausgabe Verweis Parameter, z. – `int&` . –, `_Out_` stellt die richtige Semantik bereit.  Wenn der Ausgabewert jedoch ein Zeiger ist – z `int *&` . –, stellen die entsprechenden Zeiger Anmerkungen wie `_Outptr_ int **` nicht die richtige Semantik bereit.  Verwenden Sie die folgenden zusammengesetzten Anmerkungen, um die Semantik der Ausgabe Verweis Parameter für Zeiger Typen kurz auszudrücken:  
  
 **Anmerkungen und Beschreibungen**  
  
- `_Outref_`  
  
     Das Ergebnis muss im Post-State gültig sein und darf nicht NULL sein.  
  
- `_Outref_result_maybenull_`  
  
     Das Ergebnis muss im Post-State gültig sein, kann jedoch im Post-State NULL sein.  
  
- `_Outref_result_buffer_(s)`  
  
     Das Ergebnis muss im Post-State gültig sein und darf nicht NULL sein. Zeigt auf einen gültigen Puffer von size- `s` Elementen.  
  
- `_Outref_result_bytebuffer_(s)`  
  
     Das Ergebnis muss im Post-State gültig sein und darf nicht NULL sein. Zeigt auf einen gültigen Puffer mit einer Größe von `s` Bytes.  
  
- `_Outref_result_buffer_to_(s, c)`  
  
     Das Ergebnis muss im Post-State gültig sein und darf nicht NULL sein. Zeigt auf den Puffer von `s` Elementen, von denen der erste `c` gültig ist.  
  
- `_Outref_result_bytebuffer_to_(s, c)`  
  
     Das Ergebnis muss im Post-State gültig sein und darf nicht NULL sein. Zeigt auf den Puffer von `s` bytes, von denen der erste `c` gültig ist.  
  
- `_Outref_result_buffer_all_(s)`  
  
     Das Ergebnis muss im Post-State gültig sein und darf nicht NULL sein. Verweist auf einen gültigen Puffer der `s` gültigen Größe von Elementen.  
  
- `_Outref_result_bytebuffer_all_(s)`  
  
     Das Ergebnis muss im Post-State gültig sein und darf nicht NULL sein. Verweist auf einen gültigen Puffer von `s` Bytes gültiger-Elemente.  
  
- `_Outref_result_buffer_maybenull_(s)`  
  
     Das Ergebnis muss im Post-State gültig sein, kann jedoch im Post-State NULL sein. Zeigt auf einen gültigen Puffer von size- `s` Elementen.  
  
- `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Das Ergebnis muss im Post-State gültig sein, kann jedoch im Post-State NULL sein. Zeigt auf einen gültigen Puffer mit einer Größe von `s` Bytes.  
  
- `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Das Ergebnis muss im Post-State gültig sein, kann jedoch im Post-State NULL sein. Zeigt auf den Puffer von `s` Elementen, von denen der erste `c` gültig ist.  
  
- `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Das Ergebnis muss im Post-State gültig sein, kann jedoch im Post-Zustand NULL sein. Zeigt auf den Puffer von `s` bytes, von denen der erste `c` gültig ist.  
  
- `_Outref_result_buffer_all_maybenull_(s)`  
  
     Das Ergebnis muss im Post-State gültig sein, kann jedoch im Post-Zustand NULL sein. Verweist auf einen gültigen Puffer der `s` gültigen Größe von Elementen.  
  
- `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Das Ergebnis muss im Post-State gültig sein, kann jedoch im Post-Zustand NULL sein. Verweist auf einen gültigen Puffer von `s` Bytes gültiger-Elemente.  
  
## <a name="return-values"></a>Rückgabewerte  
 Der Rückgabewert einer Funktion ähnelt einem `_Out_` Parameter, befindet sich jedoch auf einer anderen Ebene von "de-Reference", und Sie müssen das Konzept des Zeigers auf das Ergebnis nicht überprüfen.  Für die folgenden Anmerkungen ist der Rückgabewert das mit Anmerkungen versehene Objekt – ein Skalar, ein Zeiger auf eine Struktur oder ein Zeiger auf einen Puffer. Diese Anmerkungen haben die gleiche Semantik wie die entsprechende `_Out_` Anmerkung.  
  
`_Ret_z_`, `_Ret_writes_(s)`, `_Ret_writes_bytes_(s)`, `_Ret_writes_z_(s)`, `_Ret_writes_to_(s,c)`, `_Ret_writes_maybenull_(s)`, `_Ret_writes_to_maybenull_(s)`, `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`, `_Ret_maybenull_z_`, `_Ret_null_`, `_Ret_notnull_`, `_Ret_writes_bytes_to_`, `_Ret_writes_bytes_maybenull_`, `_Ret_writes_bytes_to_maybenull_`
  
## <a name="other-common-annotations"></a>Andere allgemeine Anmerkungen  
 **Anmerkungen und Beschreibungen**  
  
- `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Der Parameter, das Feld oder das Ergebnis befindet sich im Bereich (einschließlich) von `low` bis `hi` .  Entspricht dem, `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` das auf das mit Anmerkungen versehene Objekt in Verbindung mit den entsprechenden Bedingungen vor oder nach Bundesstaat angewendet wird.  
  
    > [!IMPORTANT]
    > Obwohl die Namen "in" und "out" enthalten, gilt die Semantik `_In_` von `_Out_` und **nicht** für diese Anmerkungen.  
  
- `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     Der mit Anmerkungen versehene Wert ist genau `expr` .  Entspricht dem, `_Satisfies_(_Curr_ == expr)` das auf das mit Anmerkungen versehene Objekt in Verbindung mit den entsprechenden Bedingungen vor oder nach Bundesstaat angewendet wird.  
  
- `_Struct_size_bytes_(size)`  
  
     Gilt für eine Struktur-oder Klassen Deklaration.  Gibt an, dass ein gültiges Objekt dieses Typs größer als der deklarierte Typ und mit der Anzahl von Bytes sein kann, die von angegeben werden `size` .  Beispiel:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     Die Puffergröße eines Parameters `pM` vom Typ in Byte `MyStruct *` wird dann wie folgt angenommen:  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>Zugehörige Ressourcen  
 [Blog des Code Analyseteams](https://blogs.msdn.com/b/codeanalysis/)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Sal-Anmerkungen zum Reduzieren von C/C++-Code Fehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Grundlegendes zur SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperr Verhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung angewendet wird](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Intrinsische Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)

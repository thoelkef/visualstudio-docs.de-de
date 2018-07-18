---
title: Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 8c6c5147bdb1720c6da20dd93dd3bda81c2e6464
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900445"
---
# <a name="annotating-function-parameters-and-return-values"></a>Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten
Dieser Artikel beschreibt typische Verwendungen von Anmerkungen für einfache Funktionsparameter – skalare und Zeigern auf Strukturen und Klassen – und die meisten Arten von Puffern.  Dieser Artikel zeigt auch die gängigsten Verwendungsmuster für Anmerkungen. Zusätzliche Anmerkungen, die mit Funktionen verknüpft sind, finden Sie unter [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)

## <a name="pointer-parameters"></a>Zeigerparameter
 Für die Anmerkungen in der folgenden Tabelle Wenn ein Zeigerparameter kommentiert wird ist, meldet der Analyzer einen Fehler, wenn der Zeiger null ist.  Dies gilt für Zeiger und für jedes Datenelement, auf das.

 **Anmerkungen und Beschreibungen**

-   `_In_`

     Merkt Eingabeparameter, die skalare, Strukturen, Zeigern auf Strukturen und Like sind.  Explizit kann auf einfache skalare verwendet werden.  Der Parameter muss gültig sein, in dem Zustand vor und wird nicht geändert werden.

-   `_Out_`

     Merkt Output-Parameter, die skalare, Strukturen, Zeigern auf Strukturen und Like sind.  Wenden Sie dies nicht auf ein Objekt, das einen Wert zurückgeben kann – z. B. ein Skalarwert, der als Wert übergeben wird.  Der Parameter besitzt kein vor Status gültig ist, aber es muss gültig sein, nach der Status.

-   `_Inout_`

     Fügt einen Parameter, der von der Funktion geändert werden.  Er muss gültig sein, in dem Zustand vor und nach der Status wird allerdings wird davon ausgegangen, dass Sie verschiedene Werte vor und nach dem Aufruf besitzen. Muss für einen änderbaren Wert gelten.

-   `_In_z_`

     Ein Zeiger auf eine auf Null endende Zeichenfolge, die als Eingabe verwendet wird.  Die Zeichenfolge muss vor Status gültig sein.  Varianten der `PSTR`, die bereits richtigen Anmerkungen aufweisen, als bevorzugt eingestuft.

-   `_Inout_z_`

     Ein Zeiger auf ein Zeichenarray mit Null endende, die geändert werden soll.  Es muss gültig sein, vor und nach dem Aufruf, jedoch wird angenommen, dass des Werts geändert haben.  Das null-Abschlusszeichen verschoben werden kann, aber nur die Elemente bis zu den ursprünglichen null-Terminator zugegriffen werden können.

-   `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Ein Zeiger auf ein Array, das von der Funktion gelesen wird.  Das Array der Größe ist `s` Elemente, von denen alle muss gültig sein.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes anstelle von Elementen. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Beispielsweise `char` Zeichenfolgen verwenden würden die `_bytes_` Variante nur, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_In_reads_z_(s)`

     Ein Zeiger auf ein Array, das Null-terminierte und verfügt über eine bekannte Größe. Die Elemente bis zu dem null-Abschlusszeichen – oder `s` Wenn kein null-Abschlusszeichen vorhanden ist, muss gültig sein, in dem Zustand vor.  Wenn die Größe in Byte bekannt ist, zu skalieren `s` von der Elementgröße.

-   `_In_reads_or_z_(s)`

     Ein Zeiger auf ein Array, das Null-terminierte oder verfügt über eine bekannte Größe oder beides. Die Elemente bis zu dem null-Abschlusszeichen – oder `s` Wenn kein null-Abschlusszeichen vorhanden ist, muss gültig sein, in dem Zustand vor.  Wenn die Größe in Byte bekannt ist, zu skalieren `s` von der Elementgröße.  (Verwendet für die `strn` Familie.)

-   `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Ein Zeiger auf ein Array von `s` Elemente (bzw. Bytes), die von der Funktion geschrieben werden.  Die Elemente des Arrays müssen nicht im Zustand vor gültig sein, und die Anzahl der Elemente, die nach der Status gültig sind, ist nicht angegeben.  Wenn für den Parametertyp Anmerkungen sind, werden sie nach der Status angewendet. Betrachten Sie hierzu den folgenden Beispielcode:

     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`

     In diesem Beispiel stellt der Aufrufer einen Puffer bereit, mit denen `size` Elemente für `p1`.  `MyStringCopy` stellt einige dieser Elemente ungültig. Vor allem die `_Null_terminated_` Anmerkung zum `PWSTR` bedeutet, dass `p1` nach der Status ist Null-terminiert.  Auf diese Weise die Anzahl von gültigen Elementen ist immer noch klar definierten, eine bestimmtes Elementanzahl ist jedoch nicht erforderlich.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes anstelle von Elementen. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Beispielsweise `char` Zeichenfolgen verwenden würden die `_bytes_` Variante nur, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_Out_writes_z_(s)`

     Ein Zeiger auf ein Array von `s` Elemente.  Die Elemente müssen nicht im Zustand vor gültig sein.  Nach der Status, die Elemente sich über den null-Terminator – vorhanden sein muss, muss gültig sein.  Wenn die Größe in Byte bekannt ist, zu skalieren `s` von der Elementgröße.

-   `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Ein Zeiger auf ein Array, das sowohl gelesen und in der Funktion geschrieben.  Ist Größe `s` Elemente, in vor und nach der Zustand und gültig.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes anstelle von Elementen. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Beispielsweise `char` Zeichenfolgen verwenden würden die `_bytes_` Variante nur, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_Inout_updates_z_(s)`

     Ein Zeiger auf ein Array, das Null-terminierte und verfügt über eine bekannte Größe. Die Elemente von über den null-Terminator – vorhanden sein muss, muss gültig sein, in dem Zustand vor und nach der Status.  Der Wert in der nach der Status wird davon ausgegangen, dass ungleich dem Wert im Status "vor" sein; Dies schließt den Speicherort der null-Abschlusszeichen. Wenn die Größe in Byte bekannt ist, zu skalieren `s` von der Elementgröße.

-   `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Ein Zeiger auf ein Array von `s` Elemente.  Die Elemente müssen nicht im Zustand vor gültig sein.  Nach der Status, die Elemente bis zu der `c`- th-Element muss gültig sein.  Skalieren Sie die Größe in Byte bekannt, `s` und `c` vom Elementgröße oder Verwenden der `_bytes_` Variant-Wert, der als definiert ist:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     In anderen Worten, jedes Element, das in den Puffer vorhanden, bis zu `s` im Status "vor" gilt im Status "POST".  Zum Beispiel:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

-   `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Ein Zeiger auf ein Array, das sowohl gelesen und werden, von der Funktion geschrieben.  Ist Größe `s` Elemente, die geklont werden gültige vor, und `c` Elemente müssen nach der Status gültig sein.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes anstelle von Elementen. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Beispielsweise `char` Zeichenfolgen verwenden würden die `_bytes_` Variante nur, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_Inout_updates_z_(s)`

     Ein Zeiger auf ein Array, das Null-terminierte und verfügt über eine bekannte Größe. Die Elemente von über den null-Terminator – vorhanden sein muss, muss gültig sein, in dem Zustand vor und nach der Status.  Der Wert in der nach der Status wird davon ausgegangen, dass ungleich dem Wert im Status "vor" sein; Dies schließt den Speicherort der null-Abschlusszeichen. Wenn die Größe in Byte bekannt ist, zu skalieren `s` von der Elementgröße.

-   `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Ein Zeiger auf ein Array von `s` Elemente.  Die Elemente müssen nicht im Zustand vor gültig sein.  Nach der Status, die Elemente bis zu der `c`- th-Element muss gültig sein.  Skalieren Sie die Größe in Byte bekannt, `s` und `c` vom Elementgröße oder Verwenden der `_bytes_` Variant-Wert, der als definiert ist:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     In anderen Worten, jedes Element, das in den Puffer vorhanden, bis zu `s` im Status "vor" gilt im Status "POST".  Zum Beispiel:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

-   `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Ein Zeiger auf ein Array, das sowohl gelesen und werden, von der Funktion geschrieben.  Ist Größe `s` Elemente, die geklont werden gültige vor, und `c` Elemente müssen nach der Status gültig sein.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes anstelle von Elementen. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Beispielsweise `char` Zeichenfolgen verwenden würden die `_bytes_` Variante nur, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Ein Zeiger auf ein Array, das sowohl gelesen und werden, von der Funktion der Größe geschrieben `s` Elemente. Definiert als äquivalent zu:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     In anderen Worten, jedes Element, das in den Puffer vorhanden, bis zu `s` im Status "vor" ist ungültig in den Zustand vor und nach der Zustand.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes anstelle von Elementen. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Beispielsweise `char` Zeichenfolgen verwenden würden die `_bytes_` Variante nur, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_In_reads_to_ptr_(p)`

     Ein Zeiger auf ein Array für die der Ausdruck `p`  -  `_Curr_` (d. h. `p` minus `_Curr_`) wird durch die entsprechende Sprache standard definiert.  Die Elemente vor `p` muss gültig sein, in dem Zustand vor.

-   `_In_reads_to_ptr_z_(p)`

     Ein Zeiger auf ein mit Null endendes Array für die der Ausdruck `p`  -  `_Curr_` (d. h. `p` minus `_Curr_`) wird durch die entsprechende Sprache standard definiert.  Die Elemente vor `p` muss gültig sein, in dem Zustand vor.

-   `_Out_writes_to_ptr_(p)`

     Ein Zeiger auf ein Array für die der Ausdruck `p`  -  `_Curr_` (d. h. `p` minus `_Curr_`) wird durch die entsprechende Sprache standard definiert.  Die Elemente vor `p` müssen nicht im Zustand vor gültig sein und muss nach der Status gültig sein.

-   `_Out_writes_to_ptr_z_(p)`

     Ein Zeiger auf ein mit Null endendes Array für die der Ausdruck `p`  -  `_Curr_` (d. h. `p` minus `_Curr_`) wird durch die entsprechende Sprache standard definiert.  Die Elemente vor `p` müssen nicht im Zustand vor gültig sein und muss nach der Status gültig sein.

## <a name="optional-pointer-parameters"></a>Optionale Zeigerparameter
 Wenn ein Zeiger parameteranmerkung enthält `_opt_`, bedeutet dies, dass der Parameter null sein kann. Andernfalls die Anmerkung führt identisch mit der Version, die keine `_opt_`. Im folgenden wird eine Liste der `_opt_` Varianten der Zeiger Parameter Anmerkungen:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Ausgabezeigerparameter
 Ausgabe Zeigerparametern erfordern besondere Schreibweise um Null-Funktion auf den Parameter und den Speicherort verweist, zu unterscheiden.

 **Anmerkungen und Beschreibungen**

-   `_Outptr_`

     Parameter darf nicht null sein und im Status "POST" der Speicherort verweist, darf nicht null sein und muss gültig sein.

-   `_Outptr_opt_`

     Parameter kann null sein, aber im Status "POST" der Speicherort verweist, darf nicht null sein und muss gültig sein.

-   `_Outptr_result_maybenull_`

     Parameter darf nicht null sein, und im Status "POST" der Speicherort auf null sein kann.

-   `_Outptr_opt_result_maybenull_`

     Parameter kann null sein, und im Status "POST" der Speicherort auf null sein kann.

 In der folgenden Tabelle werden zusätzliche Teilzeichenfolgen in der Anmerkungsname genauer die Bedeutung der Anmerkung eingefügt.  Die verschiedenen Teilzeichenfolgen sind `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, und `_to_`.

> [!IMPORTANT]
>  Ist die Schnittstelle, die betreffenden COM, verwenden Sie das COM-Format dieser Anmerkungen. Verwenden Sie die COM-Anmerkungen nicht mit einer beliebigen anderen Typschnittstelle.

 **Anmerkungen und Beschreibungen**

-   `_Outptr_result_z_`

     `_Outptr_opt_result_z_`

     `_Outptr_result_maybenull_z_`

     `_Ouptr_opt_result_maybenull_z_`

     Der zurückgegebene Zeiger hat die `_Null_terminated_` Anmerkung.

-   `_COM_Outptr_`

     `_COM_Outptr_opt_`

     `_COM_Outptr_result_maybenull_`

     `_COM_Outptr_opt_result_maybenull_`

     Der zurückgegebene Zeiger verfügt über COM-Semantik, und Sie aus diesem Grund enthält ein `_On_failure_` nach der Bedingung, dass der zurückgegebene Zeiger null ist.

-   `_Outptr_result_buffer_(s)`

     `_Outptr_result_bytebuffer_(s)`

     `_Outptr_opt_result_buffer_(s)`

     `_Outptr_opt_result_bytebuffer_(s)`

     Der zurückgegebene Zeiger verweist auf eine gültige Puffer mit einer Größe `s` Elemente oder Bytes.

-   `_Outptr_result_buffer_to_(s, c)`

     `_Outptr_result_bytebuffer_to_(s, c)`

     `_Outptr_opt_result_buffer_to_(s,c)`

     `_Outptr_opt_result_bytebuffer_to_(s,c)`

     Der zurückgegebene Zeiger verweist auf einen Puffer mit einer Größe `s` Elemente oder Bytes, von denen das erste `c` gültig sind.

 Bestimmte Konventionen in Schnittstelle annehmen, dass die Output-Parameter bei einem Fehler nullified sind.  Mit Ausnahme von explizit COM-Code werden die Formen in der folgenden Tabelle bevorzugt.  Verwenden Sie die entsprechenden COM-Formen, die aufgeführt sind für COM-Code im vorherigen Abschnitt.

 **Anmerkungen und Beschreibungen**

-   `_Result_nullonfailure_`

     Ändert die andere Anmerkungen. Das Resultset ist null, wenn die Funktion fehlerhaft ist.

-   `_Result_zeroonfailure_`

     Ändert die andere Anmerkungen. Das Ergebnis wird auf 0 (null) festgelegt, wenn die Funktion fehlschlägt.

-   `_Outptr_result_nullonfailure_`

     Der zurückgegebene Zeiger verweist auf einen gültigen Puffer, wenn die Funktion erfolgreich ausgeführt wird, oder Null, wenn die Funktion fehlschlägt. Diese Anmerkung ist für ein nicht Optionaler Parameter.

-   `_Outptr_opt_result_nullonfailure_`

     Der zurückgegebene Zeiger verweist auf einen gültigen Puffer, wenn die Funktion erfolgreich ausgeführt wird, oder Null, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen optionalen Parameter.

-   `_Outref_result_nullonfailure_`

     Der zurückgegebene Zeiger verweist auf einen gültigen Puffer, wenn die Funktion erfolgreich ausgeführt wird, oder Null, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen Verweisparameter.

## <a name="output-reference-parameters"></a>Ausgabeverweisparameter
 Eine übliche Verwendung des Verweisparameters ist für Output-Parameter.  Für einfache ausgabeverweisparameter – z. B. `int&`–`_Out_` stellt die korrekte Semantik.  Wenn der Ausgabewert ist jedoch ein Zeiger – z. B. `int *&`– wie die entsprechende Zeiger Anmerkungen `_Outptr_ int **` nicht die richtige Semantik bereitstellen.  Um die Semantik der ausgabeverweisparameter für Zeigertypen deutlicher auszudrücken, verwenden Sie diese zusammengesetzten Anmerkungen:

 **Anmerkungen und Beschreibungen**

-   `_Outref_`

     Ergebnis nach der Status gültig sein und darf nicht null sein.

-   `_Outref_result_maybenull_`

     Ergebnis muss nach der Status gültig sein, aber nach der Status möglicherweise null.

-   `_Outref_result_buffer_(s)`

     Ergebnis nach der Status gültig sein und darf nicht null sein. Verweist auf gültige Puffer mit einer Größe `s` Elemente.

-   `_Outref_result_bytebuffer_(s)`

     Ergebnis nach der Status gültig sein und darf nicht null sein. Verweist auf gültige Puffer mit einer Größe `s` Bytes.

-   `_Outref_result_buffer_to_(s, c)`

     Ergebnis nach der Status gültig sein und darf nicht null sein. Verweist auf Puffer `s` Elemente, von denen das erste `c` gültig sind.

-   `_Outref_result_bytebuffer_to_(s, c)`

     Ergebnis nach der Status gültig sein und darf nicht null sein. Verweist auf Puffer `s` Bytes, von denen das erste `c` gültig sind.

-   `_Outref_result_buffer_all_(s)`

     Ergebnis nach der Status gültig sein und darf nicht null sein. Verweist auf gültige Puffer mit einer Größe `s` gültigen Elementen.

-   `_Outref_result_bytebuffer_all_(s)`

     Ergebnis nach der Status gültig sein und darf nicht null sein. Verweist auf gültige Puffer `s` Bytes von gültigen Elementen.

-   `_Outref_result_buffer_maybenull_(s)`

     Ergebnis muss nach der Status gültig sein, aber nach der Status möglicherweise null. Verweist auf gültige Puffer mit einer Größe `s` Elemente.

-   `_Outref_result_bytebuffer_maybenull_(s)`

     Ergebnis muss nach der Status gültig sein, aber nach der Status möglicherweise null. Verweist auf gültige Puffer mit einer Größe `s` Bytes.

-   `_Outref_result_buffer_to_maybenull_(s, c)`

     Ergebnis muss nach der Status gültig sein, aber nach der Status möglicherweise null. Verweist auf Puffer `s` Elemente, von denen das erste `c` gültig sind.

-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Ergebnis muss gültig sein, nach der Status, aber es kann null sein, im Post-Zustand. Verweist auf Puffer `s` Bytes, von denen das erste `c` gültig sind.

-   `_Outref_result_buffer_all_maybenull_(s)`

     Ergebnis muss gültig sein, nach der Status, aber es kann null sein, im Post-Zustand. Verweist auf gültige Puffer mit einer Größe `s` gültigen Elementen.

-   `_Outref_result_bytebuffer_all_maybenull_(s)`

     Ergebnis muss gültig sein, nach der Status, aber es kann null sein, im Post-Zustand. Verweist auf gültige Puffer `s` Bytes von gültigen Elementen.

## <a name="return-values"></a>Rückgabewerte
 Der Rückgabewert einer Funktion ähnelt einer `_Out_` Parameter ist jedoch auf einer anderen De-reference, und Sie müssen das Konzept des Zeigers auf das Ergebnis zu berücksichtigen.  Für die folgenden Anmerkungen der Rückgabewert ist das Objekt mit Anmerkungen – ein Skalarwert, ein Zeiger auf eine Struktur oder ein Zeiger auf einen Puffer. Diese Anmerkungen weisen die gleiche Semantik wie die entsprechende `_Out_` Anmerkung.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="other-common-annotations"></a>Andere allgemeine Anmerkungen
 **Anmerkungen und Beschreibungen**

-   `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Die Parameter, ein Feld oder Ergebnis wird im Bereich (inklusiv) von `low` auf `hi`.  Entspricht `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` , für das Objekt mit Anmerkungen, zusammen mit den entsprechenden vorab Status "bzw." nach dem Status Bedingungen angewendet wird.

    > [!IMPORTANT]
    >  Obwohl die Namen "in" und "out", die Semantik der enthalten `_In_` und `_Out_` führen **nicht** gelten für diese Anmerkungen.

-   `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     Der kommentierte Wert ist genau `expr`.  Entspricht `_Satisfies_(_Curr_ == expr)` , für das Objekt mit Anmerkungen, zusammen mit den entsprechenden vorab Status "bzw." nach dem Status Bedingungen angewendet wird.

-   `_Struct_size_bytes_(size)`

     Gilt für eine Deklaration Struct "oder"-Klasse.  Gibt an, dass ein gültiges Objekt dieses Typs möglicherweise größer als der deklarierte Typ mit der Anzahl von Bytes wird, indem `size`.  Zum Beispiel:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     Die Puffergröße in Bytes eines Parameters `pM` des Typs `MyStruct *` wird dann ausgeführt werden:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Verwandte Ressourcen
 [Code Analysis-Teamblog](http://go.microsoft.com/fwlink/?LinkId=251197)

## <a name="see-also"></a>Siehe auch
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [Grundlegendes zu SAL](../code-quality/understanding-sal.md) [Funktionsverhalten](../code-quality/annotating-function-behavior.md) [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md) [ Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md) [angeben, wann und wo eine Anmerkung gültig](../code-quality/specifying-when-and-where-an-annotation-applies.md) [systeminterne Funktionen](../code-quality/intrinsic-functions.md) [empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
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
ms.openlocfilehash: ae4fcfa442f648126a93d1ec6a3b0d3c4fc7c981
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924823"
---
# <a name="annotating-function-parameters-and-return-values"></a>Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten
Dieser Artikel beschreibt typische Verwendungen von Anmerkungen für die einfache Funktionsparameter, skalare und Verweise auf Strukturen und Klassen, und die meisten Arten von Puffern.  Dieser Artikel zeigt außerdem gängige Verwendungsmuster für Anmerkungen. Zusätzliche Anmerkungen, die mit Funktionen verknüpft sind, finden Sie unter [Funktionsverhalten kommentieren](../code-quality/annotating-function-behavior.md)

## <a name="pointer-parameters"></a>Zeigerparameter
 Für die Anmerkungen in der folgenden Tabelle wenn der Parameter ein Zeiger kommentiert wird ist, der Analyzer ein Fehler gemeldet, wenn der Zeiger null ist.  Dies gilt für Zeiger und an ein Datenelement, das auf die gezeigt wird.

 **Anmerkungen und Beschreibungen**

-   `_In_`

     Kommentiert von Eingabeparametern, die skalare, Strukturen, Zeigern auf Strukturen usw. sind.  Explizit kann auf einfache skalare verwendet werden.  Der Parameter muss vor Status gültig sein und wird nicht geändert werden.

-   `_Out_`

     Kommentiert die Output-Parameter, die skalare, Strukturen, Zeigern auf Strukturen und ähnliches.  Wenden Sie dies nicht auf ein Objekt, das kann keinen Wert zurückgeben, z. B. ein Skalarwert, der als Wert übergeben wird.  Der Parameter keine erforderliche Status gültig ist, jedoch muss gültig sein, nach dem Status.

-   `_Inout_`

     Kommentiert die Parameter, der von der Funktion geändert werden.  Es muss gültig sein, vor Zustand und nach dem Zustand, aber es wird davon ausgegangen, dass unterschiedliche Werte aufweisen, vor und nach dem Aufruf. Muss ein änderbarer Wert zuweisen.

-   `_In_z_`

     Ein Zeiger auf eine auf Null endende Zeichenfolge, die als Eingabe verwendet wird.  Die Zeichenfolge muss vor Status gültig sein.  Varianten der `PSTR`, die bereits die richtigen Anmerkungen haben, als bevorzugt eingestuft.

-   `_Inout_z_`

     Ein Zeiger auf ein Array von Null-terminierte Zeichen, die geändert wird.  Es muss gültig sein, vor und nach dem Aufruf, jedoch wird davon ausgegangen, dass des Werts geändert haben.  Der null-Terminator verschoben werden kann, aber nur die Elemente bis zu der ursprünglichen null-Terminator zugegriffen werden können.

-   `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Ein Zeiger auf ein Array, die von der Funktion gelesen wird.  Das Array hat eine Größe `s` Elemente, die alle muss gültig sein.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes, die keine Elemente. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden würden die `_bytes_` Variant-Wert nur dann, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_In_reads_z_(s)`

     Ein Zeiger auf ein Array, das Null-terminiert ist, und verfügt über eine bekannte Größe. Elemente bis zu dem null-Abschlusszeichen – oder `s` , wenn kein null-Abschlusszeichen vorhanden ist, muss vor Status gültig sein.  Wenn die Größe in Byte bekannt ist, skalieren `s` mit der Elementgröße.

-   `_In_reads_or_z_(s)`

     Ein Zeiger auf ein Array, das Null-terminiert oder verfügt über eine bekannte Größe oder beides. Elemente bis zu dem null-Abschlusszeichen – oder `s` , wenn kein null-Abschlusszeichen vorhanden ist, muss vor Status gültig sein.  Wenn die Größe in Byte bekannt ist, skalieren `s` mit der Elementgröße.  (Verwendet für die `strn` Familie.)

-   `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Ein Zeiger auf ein Array von `s` Elemente (bzw. Bytes), die von der Funktion geschrieben werden.  Die Elemente des Arrays müssen nicht vorab Status gültig sein, und die Anzahl der Elemente, die nach dem Status gültig sind, ist nicht angegeben.  Wenn Anmerkungen für den Parametertyp sind, werden sie nach dem Status angewendet. Betrachten Sie hierzu den folgenden Beispielcode:

     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`

     In diesem Beispiel stellt der Aufrufer einen Puffer von `size` Elemente für `p1`.  `MyStringCopy` lassen sich einige dieser Elemente gültig. Noch wichtiger ist, dass die `_Null_terminated_` Anmerkung zu `PWSTR` bedeutet, dass `p1` nach der Status wird auf Null endet.  Klicken Sie auf diese Weise können die Anzahl von gültigen Elementen ist dennoch klar definierte, aber eine bestimmtes Element-Anzahl ist nicht erforderlich.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes, die keine Elemente. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden würden die `_bytes_` Variant-Wert nur dann, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_Out_writes_z_(s)`

     Ein Zeiger auf ein Array von `s` Elemente.  Die Elemente müssen nicht vorab Status gültig sein.  Nach der Status, die Elemente nach oben durch den null-Terminator – vorhanden sein muss, muss gültig sein.  Wenn die Größe in Byte bekannt ist, skalieren `s` mit der Elementgröße.

-   `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Ein Zeiger auf ein Array, das sowohl lesen als auch in der Funktion geschrieben.  Es ist Größe `s` Elemente, und in vor und nach der gültig.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes, die keine Elemente. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden würden die `_bytes_` Variant-Wert nur dann, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_Inout_updates_z_(s)`

     Ein Zeiger auf ein Array, das Null-terminiert ist, und verfügt über eine bekannte Größe. Die Elemente nach oben durch den null-Terminator – vorhanden sein muss, muss vor Zustand und nach dem Zustand gültig sein.  Der Wert in der nach der Status wird davon ausgegangen, dass sich von den Wert im Zustand "vor"; Dies schließt den Speicherort der null-Abschlusszeichen. Wenn die Größe in Byte bekannt ist, skalieren `s` mit der Elementgröße.

-   `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Ein Zeiger auf ein Array von `s` Elemente.  Die Elemente müssen nicht vorab Status gültig sein.  Nach der Status, die Elemente bis zu der `c`- th-Element muss gültig sein.  Wenn die Größe in Byte bekannt ist, skalieren `s` und `c` durch die Elementgröße oder die Verwendung der `_bytes_` Variante, die folgendermaßen definiert ist:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     Das heißt, jedes Element, das im Puffer vorhanden, bis zu `s` im Zustand "vor" gilt im Zustand "POST".  Zum Beispiel:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

-   `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Ein Zeiger auf ein Array, das sowohl gelesen und werden, von der Funktion geschrieben.  Es ist Größe `s` alle gültig in vor-Zustand sein muss, Elemente und `c` Elemente müssen gültig sein, nach dem Status.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes, die keine Elemente. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden würden die `_bytes_` Variant-Wert nur dann, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_Inout_updates_z_(s)`

     Ein Zeiger auf ein Array, das Null-terminiert ist, und verfügt über eine bekannte Größe. Die Elemente nach oben durch den null-Terminator – vorhanden sein muss, muss vor Zustand und nach dem Zustand gültig sein.  Der Wert in der nach der Status wird davon ausgegangen, dass sich von den Wert im Zustand "vor"; Dies schließt den Speicherort der null-Abschlusszeichen. Wenn die Größe in Byte bekannt ist, skalieren `s` mit der Elementgröße.

-   `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Ein Zeiger auf ein Array von `s` Elemente.  Die Elemente müssen nicht vorab Status gültig sein.  Nach der Status, die Elemente bis zu der `c`- th-Element muss gültig sein.  Wenn die Größe in Byte bekannt ist, skalieren `s` und `c` durch die Elementgröße oder die Verwendung der `_bytes_` Variante, die folgendermaßen definiert ist:

     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`

     Das heißt, jedes Element, das im Puffer vorhanden, bis zu `s` im Zustand "vor" gilt im Zustand "POST".  Zum Beispiel:

     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`

-   `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Ein Zeiger auf ein Array, das sowohl gelesen und werden, von der Funktion geschrieben.  Es ist Größe `s` alle gültig in vor-Zustand sein muss, Elemente und `c` Elemente müssen gültig sein, nach dem Status.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes, die keine Elemente. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden würden die `_bytes_` Variant-Wert nur dann, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Ein Zeiger auf ein Array, das sowohl gelesen und werden, von der Funktion der Größe geschrieben `s` Elemente. Definiert als äquivalent zu:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     Das heißt, jedes Element, das im Puffer vorhanden, bis zu `s` im Zustand "vor" gilt im Zustand der vor und nach dem Status.

     Die `_bytes_` Variant-Wert gibt die Größe in Bytes, die keine Elemente. Verwenden Sie diese Option aus, nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden würden die `_bytes_` Variant-Wert nur dann, wenn eine ähnliche Funktion verwendet `wchar_t` würde.

-   `_In_reads_to_ptr_(p)`

     Ein Zeiger auf ein Array für die der Ausdruck `p`  -  `_Curr_` (d. h. `p` minus `_Curr_`) wird von der entsprechenden Sprache standard definiert.  Die Elemente vor `p` muss vor Status gültig sein.

-   `_In_reads_to_ptr_z_(p)`

     Ein Zeiger auf eine mit Null endendes Array für die der Ausdruck `p`  -  `_Curr_` (d. h. `p` minus `_Curr_`) wird von der entsprechenden Sprache standard definiert.  Die Elemente vor `p` muss vor Status gültig sein.

-   `_Out_writes_to_ptr_(p)`

     Ein Zeiger auf ein Array für die der Ausdruck `p`  -  `_Curr_` (d. h. `p` minus `_Curr_`) wird von der entsprechenden Sprache standard definiert.  Die Elemente vor `p` müssen nicht vorab Status gültig sein und muss gültig sein, nach dem Status.

-   `_Out_writes_to_ptr_z_(p)`

     Ein Zeiger auf eine mit Null endendes Array für die der Ausdruck `p`  -  `_Curr_` (d. h. `p` minus `_Curr_`) wird von der entsprechenden Sprache standard definiert.  Die Elemente vor `p` müssen nicht vorab Status gültig sein und muss gültig sein, nach dem Status.

## <a name="optional-pointer-parameters"></a>Optionale Zeigerparameter
 Wenn ein Zeiger parameteranmerkung enthält `_opt_`, bedeutet dies, dass der Parameter null sein kann. Andernfalls die Anmerkung führt die identisch mit der Version, die keine `_opt_`. Hier ist eine Liste mit den `_opt_` Varianten der Zeiger Parameter Anmerkungen:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Ausgabezeigerparameter
 Ausgabeparameter für die Zeiger erfordern besondere Schreibweise für Null-Funktion für den Parameter und den Speicherort auf eindeutig zu machen.

 **Anmerkungen und Beschreibungen**

- `_Outptr_`

   Parameter darf nicht null sein, und klicken Sie im Zustand "POST" der Speicherort verweist, darf nicht null sein, und muss gültig sein.

- `_Outptr_opt_`

   Parameter kann null sein, aber im Zustand "POST" der Speicherort verweist, darf nicht null sein und muss gültig sein.

- `_Outptr_result_maybenull_`

   Parameter darf nicht null sein, und im Zustand "nach" kann der Speicherort auf null sein.

- `_Outptr_opt_result_maybenull_`

   Parameter kann null sein, und im Zustand "nach" kann der Speicherort auf null sein.

  In der folgenden Tabelle werden zusätzliche Teilzeichenfolgen in der Anmerkungsname, der die Bedeutung der Anmerkung genauer bestimmen eingefügt.  Die verschiedenen Teilzeichenfolgen sind `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, und `_to_`.

> [!IMPORTANT]
>  Wenn die Schnittstelle, die Sie kommentieren sind COM ist, verwenden Sie com-Form von diese Anmerkungen. Verwenden Sie die COM-Anmerkungen nicht mit einer beliebigen anderen Typschnittstelle.

 **Anmerkungen und Beschreibungen**

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Ouptr_opt_result_maybenull_z_`

   Der zurückgegebene Zeiger wurde die `_Null_terminated_` Anmerkung.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   Der zurückgegebene Zeiger verfügt über eine COM-Semantik, und Sie aus diesem Grund enthält ein `_On_failure_` nach der Bedingung, dass der zurückgegebene Zeiger null ist.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   Der zurückgegebene Zeiger verweist auf einen gültigen Puffer der Größe `s` Elemente oder Bytes.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   Der zurückgegebene Zeiger verweist auf einen Puffer der Größe `s` Elemente oder Bytes, von denen die erste `c` gültig sind.

  Bestimmte Konventionen für die Schnittstelle wird davon ausgegangen, dass die Output-Parameter bei einem Fehler sitzungstokenwert sind.  Mit Ausnahme der explizit COM-Code werden die Formulare in der folgenden Tabelle bevorzugt.  Verwenden Sie für COM-Code die entsprechenden COM-Formate, die aufgeführt sind, im vorherigen Abschnitt.

  **Anmerkungen und Beschreibungen**

- `_Result_nullonfailure_`

   Ändert die andere Anmerkungen. Das Resultset ist null, wenn die Funktion fehlerhaft ist.

- `_Result_zeroonfailure_`

   Ändert die andere Anmerkungen. Das Ergebnis wird auf 0 (null) festgelegt, wenn die Funktion fehlschlägt.

- `_Outptr_result_nullonfailure_`

   Der zurückgegebene Zeiger verweist auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder Null, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen nicht optionale Parameter.

- `_Outptr_opt_result_nullonfailure_`

   Der zurückgegebene Zeiger verweist auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder Null, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen optionalen Parameter.

- `_Outref_result_nullonfailure_`

   Der zurückgegebene Zeiger verweist auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder Null, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen Verweisparameter.

## <a name="output-reference-parameters"></a>Ausgabeverweisparameter
 Eine häufige Verwendung des Verweisparameters ist für Output-Parameter.  Für einfache ausgabeverweisparametern – z. B. `int&`–`_Out_` liefert die Semantik richtig.  Wenn der Ausgabewert ist jedoch ein Zeiger, z. B. `int *&`– wie die entsprechende Zeiger Anmerkungen `_Outptr_ int **` nicht die richtige Semantik bereitstellen.  Die Semantik der ausgabeverweisparametern für Zeigertypen präzise ausgedrückt werden, verwenden Sie diese zusammengesetzten Anmerkungen:

 **Anmerkungen und Beschreibungen**

-   `_Outref_`

     Ergebnis muss nach dem Status gültig sein und darf nicht null sein.

-   `_Outref_result_maybenull_`

     Ergebnis muss gültig sein, nach der Status, aber es kann null sein, nach dem Status.

-   `_Outref_result_buffer_(s)`

     Ergebnis muss nach dem Status gültig sein und darf nicht null sein. Zeigt auf gültigen Puffer der Größe `s` Elemente.

-   `_Outref_result_bytebuffer_(s)`

     Ergebnis muss nach dem Status gültig sein und darf nicht null sein. Zeigt auf gültigen Puffer der Größe `s` Bytes.

-   `_Outref_result_buffer_to_(s, c)`

     Ergebnis muss nach dem Status gültig sein und darf nicht null sein. Verweist auf den Puffer mit `s` Elemente, von denen die erste `c` gültig sind.

-   `_Outref_result_bytebuffer_to_(s, c)`

     Ergebnis muss nach dem Status gültig sein und darf nicht null sein. Verweist auf den Puffer mit `s` Bytes, von denen die erste `c` gültig sind.

-   `_Outref_result_buffer_all_(s)`

     Ergebnis muss nach dem Status gültig sein und darf nicht null sein. Zeigt auf gültigen Puffer der Größe `s` gültigen Elementen.

-   `_Outref_result_bytebuffer_all_(s)`

     Ergebnis muss nach dem Status gültig sein und darf nicht null sein. Zeigt auf gültigen Puffer von `s` Bytes von gültigen Elementen.

-   `_Outref_result_buffer_maybenull_(s)`

     Ergebnis muss gültig sein, nach der Status, aber es kann null sein, nach dem Status. Zeigt auf gültigen Puffer der Größe `s` Elemente.

-   `_Outref_result_bytebuffer_maybenull_(s)`

     Ergebnis muss gültig sein, nach der Status, aber es kann null sein, nach dem Status. Zeigt auf gültigen Puffer der Größe `s` Bytes.

-   `_Outref_result_buffer_to_maybenull_(s, c)`

     Ergebnis muss gültig sein, nach der Status, aber es kann null sein, nach dem Status. Verweist auf den Puffer mit `s` Elemente, von denen die erste `c` gültig sind.

-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Ergebnis muss gültig sein, nach der Status, aber es kann null sein, im Post-Zustand. Verweist auf den Puffer mit `s` Bytes, von denen die erste `c` gültig sind.

-   `_Outref_result_buffer_all_maybenull_(s)`

     Ergebnis muss gültig sein, nach der Status, aber es kann null sein, im Post-Zustand. Zeigt auf gültigen Puffer der Größe `s` gültigen Elementen.

-   `_Outref_result_bytebuffer_all_maybenull_(s)`

     Ergebnis muss gültig sein, nach der Status, aber es kann null sein, im Post-Zustand. Zeigt auf gültigen Puffer von `s` Bytes von gültigen Elementen.

## <a name="return-values"></a>Rückgabewerte
 Der Rückgabewert einer Funktion ähnelt einer `_Out_` Parameter ist jedoch auf einer anderen Ebene der De-reference, und Sie müssen das Konzept des Zeigers auf das Ergebnis zu berücksichtigen.  Für die folgenden Anmerkungen, ist der Rückgabewert das mit Anmerkungen versehene Objekt – ein Skalarwert, ein Zeiger auf eine Struktur oder ein Zeiger auf einen Puffer. Diese Anmerkungen haben die gleiche Semantik wie die entsprechende `_Out_` Anmerkung.

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

     Der Parameter, ein Feld oder Ergebnis wird im Bereich (inklusiv) von `low` zu `hi`.  Äquivalent zu `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` , die auf das mit Anmerkungen versehene Objekt zusammen mit den entsprechenden vorab Zustand, oder nach dem Status Bedingungen angewendet wird.

    > [!IMPORTANT]
    >  Obwohl die Namen "in" und "out", die Semantik der enthalten `_In_` und `_Out_` führen **nicht** gelten diese Anmerkungen.

-   `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     Der mit Anmerkungen versehenen Wert `expr`.  Äquivalent zu `_Satisfies_(_Curr_ == expr)` , die auf das mit Anmerkungen versehene Objekt zusammen mit den entsprechenden vorab Zustand, oder nach dem Status Bedingungen angewendet wird.

-   `_Struct_size_bytes_(size)`

     Gilt für die Deklaration einer Struktur oder Klasse.  Gibt an, dass ein gültiges Objekt dieses Typs möglicherweise größer als der deklarierte Typ, mit der Anzahl von Bytes wird, indem `size`.  Zum Beispiel:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     Die Puffergröße in Bytes für einen Parameter `pM` des Typs `MyStruct *` wird, werden ausgeführt:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Verwandte Ressourcen
 [Code Analysis-Teamblog](http://go.microsoft.com/fwlink/?LinkId=251197)

## <a name="see-also"></a>Siehe auch
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [verstehen von SAL](../code-quality/understanding-sal.md) [Funktionsverhalten](../code-quality/annotating-function-behavior.md) [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md) [ Hinzufügen von Kommentaren Sperrverhalten](../code-quality/annotating-locking-behavior.md) [angeben, wann und wo eine Anmerkung gültig](../code-quality/specifying-when-and-where-an-annotation-applies.md) [systeminterne Funktionen](../code-quality/intrinsic-functions.md) [empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
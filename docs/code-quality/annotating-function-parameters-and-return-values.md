---
title: "Hinzuf&#252;gen einer Anmerkung zu Funktionsparametern und R&#252;ckgabewerten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Outptr_opt_result_bytebuffer_to_"
  - "_Inout_updates_all_opt_"
  - "_Post_equal_to_"
  - "_Outptr_opt_result_maybenull_"
  - "_Out_writes_bytes_all_"
  - "_Out_writes_all_opt_"
  - "_In_opt_"
  - "_Outptr_"
  - "_Outptr_result_maybenull_"
  - "_Outref_result_bytebuffer_all_maybenull_"
  - "_Inout_updates_opt_z_"
  - "_Inout_updates_z_"
  - "_Out_writes_"
  - "_Out_writes_to_ptr_opt_z_"
  - "_In_reads_to_ptr_opt_"
  - "_Ret_writes_to_maybenull_"
  - "_Outref_result_maybenull_"
  - "_Ret_writes_bytes_"
  - "_Outptr_result_bytebuffer_"
  - "_Out_writes_opt_"
  - "_Inout_updates_bytes_opt_"
  - "_In_z_"
  - "_Inout_updates_to_"
  - "_Ret_maybenull_"
  - "_Ret_writes_bytes_to_"
  - "_Ret_z_"
  - "_COM_Outptr_"
  - "_Ret_maybenull_z_"
  - "_Out_opt_"
  - "_In_reads_opt_z_"
  - "_Outptr_result_bytebuffer_to_"
  - "_Ret_notnull_"
  - "_COM_Outptr_opt_result_maybenull_"
  - "_Inout_updates_to_opt_"
  - "_Inout_updates_"
  - "_Outptr_opt_result_buffer_"
  - "_Outptr_result_buffer_to_"
  - "_Out_writes_to_ptr_opt_"
  - "_Out_writes_bytes_all_opt_"
  - "_Inout_updates_all_"
  - "_Deref_inout_range_"
  - "_Ret_writes_"
  - "_Out_writes_z_"
  - "_Ret_writes_to_"
  - "_Out_writes_to_ptr_z_"
  - "_Out_writes_bytes_to_opt_"
  - "_In_reads_or_z_"
  - "_Inout_updates_bytes_to_"
  - "_In_reads_z_"
  - "_In_opt_z_"
  - "_Outref_result_buffer_maybenull_"
  - "_Ret_range_"
  - "_COM_Outptr_opt_"
  - "_Ouptr_opt_result_maybenull_z_"
  - "_In_reads_opt_"
  - "_Inout_"
  - "_Field_range_"
  - "_Ret_writes_z_"
  - "_Out_writes_to_"
  - "_Out_writes_to_ptr_"
  - "_Inout_opt_z_"
  - "_Outref_"
  - "_Deref_out_range_"
  - "_Outref_result_buffer_"
  - "_Outref_result_buffer_to_"
  - "_Outref_result_bytebuffer_to_maybenull_"
  - "_In_reads_bytes_"
  - "_Outptr_opt_result_buffer_to_"
  - "_Outref_result_buffer_all_"
  - "_Out_writes_bytes_to_"
  - "_Result_zeroonfailure_"
  - "_In_reads_bytes_opt_"
  - "_Outref_result_buffer_to_maybenull_"
  - "_Outref_result_bytebuffer_all_"
  - "_Outref_result_buffer_all_maybenull_"
  - "_Ret_writes_maybenull_z_"
  - "_In_range_"
  - "_Inout_updates_bytes_all_opt_"
  - "_Outref_result_bytebuffer_to_"
  - "_Inout_updates_bytes_to_opt_"
  - "_Pre_equal_to_"
  - "_Ret_writes_bytes_maybenull_"
  - "_COM_Outptr_result_maybenull_"
  - "_Ret_writes_maybenull_"
  - "_Out_writes_bytes_"
  - "_Outptr_opt_"
  - "_Out_writes_opt_z_"
  - "_Outref_result_nullonfailure_"
  - "_Outptr_opt_result_z_"
  - "_Inout_opt_"
  - "_Deref_in_range_"
  - "_Outptr_result_z_"
  - "_In_reads_to_ptr_opt_z_"
  - "_Struct_size_bytes_"
  - "_Outptr_result_nullonfailure_"
  - "_In_"
  - "_Inout_updates_bytes_"
  - "_In_reads_to_ptr_z_"
  - "_Ret_writes_bytes_to_maybenull"
  - "_Outptr_opt_result_nullonfailure_"
  - "_In_reads_to_ptr_"
  - "_Outptr_result_buffer_"
  - "_Out_"
  - "_Outref_result_bytebuffer_maybenull_"
  - "_Outptr_result_maybenull_z_"
  - "_In_reads_"
  - "_Inout_updates_opt_"
  - "_Out_writes_to_opt_"
  - "_Outptr_opt_result_bytebuffer_"
  - "_Out_writes_all_"
  - "_Out_range_"
  - "_Inout_updates_bytes_all_"
  - "_Inout_z_"
  - "_Outref_result_bytebuffer_"
  - "_Result_nullonfailure_"
  - "_Ret_null_"
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Hinzuf&#252;gen einer Anmerkung zu Funktionsparametern und R&#252;ckgabewerten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Artikel beschreibt typische Verwendungen von Anmerkungen für einfache Funktionsparameter – skalare und Zeigern auf Strukturen und Klassen – und die meisten Arten von Puffern.  Dieser Artikel zeigt außerdem die gängige Verwendungsmuster für Anmerkungen. Zusätzliche Anmerkungen, die Funktionen beziehen, finden Sie unter [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>Zeigerparameter  
 Für die Anmerkungen in der folgenden Tabelle Wenn ein Zeigerparameter hinzugefügt wird, meldet das Analysemodul einen Fehler, wenn der Zeiger null ist.  Dies gilt in Zeiger und Datenelemente, auf die gezeigt wird.  
  
 **Anmerkungen und Beschreibungen**  
  
-   `_In_`  
  
     Kommentiert Eingabeparameter, die skalare, Strukturen, Zeiger auf Strukturen und ähnliches.  Explizit kann auf einfache skalare verwendet werden.  Der Parameter muss gültig sein, in dem Zustand vor und werden nicht geändert.  
  
-   `_Out_`  
  
     Kommentiert Output-Parameter, die skalare, Strukturen, Zeiger auf Strukturen und ähnliches.  Wenden Sie diese nicht auf ein Objekt, das einen Wert zurückgeben kann, z. B. ein Skalarwert, der als Wert übergeben wird.  Der Parameter keinen vor Status gültig sein, aber es muss gültig sein, nach der Status.  
  
-   `_Inout_`  
  
     Fügt einen Parameter, der von der Funktion geändert werden.  Status vor und nach der Zustand gültig sein, aber wird davon ausgegangen, dass unterschiedliche Werte vor und nach dem Aufruf. Muss auf einem änderbaren Wert anwenden.  
  
-   `_In_z_`  
  
     Ein Zeiger auf eine auf Null endende Zeichenfolge, die als Eingabe verwendet wird.  Die Zeichenfolge muss vor Status gültig sein.  Varianten des `PSTR`, die bereits die richtige Anmerkungen haben, werden bevorzugt.  
  
-   `_Inout_z_`  
  
     Ein Zeiger auf ein Zeichenarray mit Null endende, die geändert werden soll.  Es muss gültig sein, vor und nach dem Aufruf, jedoch wird angenommen, dass des Werts geändert haben.  Der null-Terminator verschoben werden kann, aber nur die Elemente bis zu den ursprünglichen null-Terminator zugegriffen werden können.  
  
-   `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     Ein Zeiger auf ein Array, das von der Funktion gelesen wird.  Das Array der Größe ist `s` Elemente, die muss gültig sein.  
  
     Die `_bytes_` Variant-Wert gibt die Größe in Byte anstatt Elemente. Verwenden Sie dies nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden die `_bytes_` mithilfe von Variant-Wert nur, wenn eine ähnliche Funktion `wchar_t` würde.  
  
-   `_In_reads_z_(s)`  
  
     Ein Zeiger auf ein Array, das Null-terminiert und verfügt über eine bekannte Größe. Elemente bis zu den null-Terminator – oder `s` wenn kein null-Abschlusszeichen vorhanden ist, muss gültig sein, in dem Zustand vor.  Wenn die Größe in Byte bekannt ist, zu skalieren `s` mit der Elementgröße.  
  
-   `_In_reads_or_z_(s)`  
  
     Ein Zeiger auf ein Array, das Null-terminiert oder eine bekannte Größe oder beides. Elemente bis zu den null-Terminator – oder `s` wenn kein null-Abschlusszeichen vorhanden ist, muss gültig sein, in dem Zustand vor.  Wenn die Größe in Byte bekannt ist, zu skalieren `s` mit der Elementgröße.  (Verwendet für die `strn` Familie.)  
  
-   `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Ein Zeiger auf ein Array von `s` Elemente (bzw. Bytes), die von der Funktion geschrieben wird.  Die Elemente des Arrays müssen nicht vorab Status gültig sein, und die Anzahl der Elemente, die nach dem Status gültig sind nicht angegeben ist.  Anmerkungen für den Parametertyp vorhanden sind, werden sie nach der Status angewendet. Betrachten Sie hierzu den folgenden Beispielcode:  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     In diesem Beispiel stellt der Aufrufer einen Puffer mit einer `size` Elemente für `p1`.  `MyStringCopy` stellt einige dieser Elemente ungültig. Noch wichtiger ist, dass die `_Null_terminated_` Anmerkung zum `PWSTR` bedeutet, dass `p1` nach der Status ist Null-terminiert.  Auf diese Weise die Anzahl der gültigen Elemente ist immer noch klar definierte, eine bestimmte Anzahl ist jedoch nicht erforderlich.  
  
     Die `_bytes_` Variant-Wert gibt die Größe in Byte anstatt Elemente. Verwenden Sie dies nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden die `_bytes_` mithilfe von Variant-Wert nur, wenn eine ähnliche Funktion `wchar_t` würde.  
  
-   `_Out_writes_z_(s)`  
  
     Ein Zeiger auf ein Array von `s` Elemente.  Die Elemente müssen nicht vorab Status gültig sein.  Nach der Status, die Elemente von über den null-Terminator – vorhanden sein muss, muss gültig sein.  Wenn die Größe in Byte bekannt ist, zu skalieren `s` mit der Elementgröße.  
  
-   `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Ein Zeiger auf ein Array, das sowohl gelesen und in der Funktion geschrieben.  Es ist der Größe `s` Elemente, und in den Zustand vor und nach der gültig.  
  
     Die `_bytes_` Variant-Wert gibt die Größe in Byte anstatt Elemente. Verwenden Sie dies nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden die `_bytes_` mithilfe von Variant-Wert nur, wenn eine ähnliche Funktion `wchar_t` würde.  
  
-   `_Inout_updates_z_(s)`  
  
     Ein Zeiger auf ein Array, das Null-terminiert und verfügt über eine bekannte Größe. Die Elemente von über den null-Terminator – vorhanden sein muss, muss gültig sein, in dem Zustand vor und nach der Status.  Der Wert in der nach der Status wird davon ausgegangen, dass von dem Wert in den Zustand vor; Dies umfasst den Speicherort der null-Abschlusszeichen. Wenn die Größe in Byte bekannt ist, zu skalieren `s` mit der Elementgröße.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Ein Zeiger auf ein Array von `s` Elemente.  Die Elemente müssen nicht vorab Status gültig sein.  Nach der Status, die Elemente bis zu den `c`-th-Element muss gültig sein.  Skalieren, wenn die Größe in Byte bekannt ist, `s` und `c` durch die Größe oder die Verwendung der `_bytes_` -Variante, die folgendermaßen definiert ist:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     In anderen Worten, jedes Element, das im Puffer vorhanden, bis zu `s` in den Zustand vor gilt in der nach der Status.  Zum Beispiel:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Ein Zeiger auf ein Array, das sowohl gelesen und, die von der Funktion geschrieben.  Es ist der Größe `s` Elemente, die muss gültig sein Zustand vor, und `c` Elemente müssen gültig sein, nach der Status.  
  
     Die `_bytes_` Variant-Wert gibt die Größe in Byte anstatt Elemente. Verwenden Sie dies nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden die `_bytes_` mithilfe von Variant-Wert nur, wenn eine ähnliche Funktion `wchar_t` würde.  
  
-   `_Inout_updates_z_(s)`  
  
     Ein Zeiger auf ein Array, das Null-terminiert und verfügt über eine bekannte Größe. Die Elemente von über den null-Terminator – vorhanden sein muss, muss gültig sein, in dem Zustand vor und nach der Status.  Der Wert in der nach der Status wird davon ausgegangen, dass von dem Wert in den Zustand vor; Dies umfasst den Speicherort der null-Abschlusszeichen. Wenn die Größe in Byte bekannt ist, zu skalieren `s` mit der Elementgröße.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Ein Zeiger auf ein Array von `s` Elemente.  Die Elemente müssen nicht vorab Status gültig sein.  Nach der Status, die Elemente bis zu den `c`-th-Element muss gültig sein.  Skalieren, wenn die Größe in Byte bekannt ist, `s` und `c` durch die Größe oder die Verwendung der `_bytes_` -Variante, die folgendermaßen definiert ist:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     In anderen Worten, jedes Element, das im Puffer vorhanden, bis zu `s` in den Zustand vor gilt in der nach der Status.  Zum Beispiel:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Ein Zeiger auf ein Array, das sowohl gelesen und, die von der Funktion geschrieben.  Es ist der Größe `s` Elemente, die muss gültig sein Zustand vor, und `c` Elemente müssen gültig sein, nach der Status.  
  
     Die `_bytes_` Variant-Wert gibt die Größe in Byte anstatt Elemente. Verwenden Sie dies nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden die `_bytes_` mithilfe von Variant-Wert nur, wenn eine ähnliche Funktion `wchar_t` würde.  
  
-   `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Ein Zeiger auf ein Array, das sowohl gelesen und werden, indem Sie die Funktion der Größe geschrieben `s` Elemente. Definiert als äquivalent zu:  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     In anderen Worten, jedes Element, das im Puffer vorhanden, bis zu `s` in den Zustand vor gilt in den Status vor und nach der Zustand.  
  
     Die `_bytes_` Variant-Wert gibt die Größe in Byte anstatt Elemente. Verwenden Sie dies nur, wenn die Größe als Elemente ausgedrückt werden kann.  Z. B. `char` Zeichenfolgen verwenden die `_bytes_` mithilfe von Variant-Wert nur, wenn eine ähnliche Funktion `wchar_t` würde.  
  
-   `_In_reads_to_ptr_(p)`  
  
     Ein Zeiger auf ein Array für die der Ausdruck `p` – `_Curr_` (d. h. `p` minus `_Curr_`) wird durch die entsprechende Sprache standard definiert.  Die Elemente vor `p` vor Status gültig sein.  
  
-   `_In_reads_to_ptr_z_(p)`  
  
     Ein Zeiger auf ein mit Null endendes Array für die der Ausdruck `p` – `_Curr_` (d. h. `p` minus `_Curr_`) wird durch die entsprechende Sprache standard definiert.  Die Elemente vor `p` vor Status gültig sein.  
  
-   `_Out_writes_to_ptr_(p)`  
  
     Ein Zeiger auf ein Array für die der Ausdruck `p` – `_Curr_` (d. h. `p` minus `_Curr_`) wird durch die entsprechende Sprache standard definiert.  Die Elemente vor `p` müssen nicht vorab Status gültig sein und muss nach dem Status gültig sein.  
  
-   `_Out_writes_to_ptr_z_(p)`  
  
     Ein Zeiger auf ein mit Null endendes Array für die der Ausdruck `p` – `_Curr_` (d. h. `p` minus `_Curr_`) wird durch die entsprechende Sprache standard definiert.  Die Elemente vor `p` müssen nicht vorab Status gültig sein und muss nach dem Status gültig sein.  
  
## <a name="optional-pointer-parameters"></a>Optionale Zeigerparameter  
 Wenn eine Zeiger parameteranmerkung enthält `_opt_`, bedeutet dies, dass der Parameter null sein kann. Andernfalls die Anmerkung führt identisch mit der Version, die umfasst `_opt_`. Hier ist eine Liste der `_opt_` Varianten Zeiger Parameter Anmerkungen:  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Ausgabezeigerparameter  
 Ausgabeparameter Zeiger erfordern besondere Schreibweise Nullwert für den Parameter und den gezeigt wird, eindeutig.  
  
 **Anmerkungen und Beschreibungen**  
  
-   `_Outptr_`  
  
     Parameter darf nicht null sein und in der nach der Status der Speicherort auf darf nicht null sein und muss gültig sein.  
  
-   `_Outptr_opt_`  
  
     Parameter kann null sein, aber im Status "POST" der Speicherort auf darf nicht null sein und muss gültig sein.  
  
-   `_Outptr_result_maybenull_`  
  
     Parameter darf nicht null sein, und in der nach der Status kann der Speicherort auf null sein.  
  
-   `_Outptr_opt_result_maybenull_`  
  
     Parameter kann null sein, und in der nach der Status kann der Speicherort auf null sein.  
  
 In der folgenden Tabelle werden zusätzliche Teilzeichenfolgen in den anmerkungsnamen genauer die Bedeutung der Anmerkung eingefügt.  Die verschiedenen Teilzeichenfolgen sind `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, und `_to_`.  
  
> [!IMPORTANT]
>  Wenn die Schnittstelle, die betreffenden COM ist, verwenden Sie com-Form von Anmerkungen. Verwenden Sie die COM-Anmerkungen nicht mit anderen Typschnittstelle.  
  
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
  
     Der zurückgegebene Zeiger hat COM-Semantik und führt daher einen `_On_failure_` nach der Bedingung, dass der zurückgegebene Zeiger null ist.  
  
-   `_Outptr_result_buffer_(s)`  
  
     `_Outptr_result_bytebuffer_(s)`  
  
     `_Outptr_opt_result_buffer_(s)`  
  
     `_Outptr_opt_result_bytebuffer_(s)`  
  
     Der zurückgegebene Zeiger verweist auf einen gültigen Puffer der Größe `s` Elemente oder Bytes.  
  
-   `_Outptr_result_buffer_to_(s, c)`  
  
     `_Outptr_result_bytebuffer_to_(s, c)`  
  
     `_Outptr_opt_result_buffer_to_(s,c)`  
  
     `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
     Der zurückgegebene Zeiger zeigt auf einen Puffer der Größe `s` Elemente oder Bytes, von denen das erste `c` gültig sind.  
  
 Bestimmte Konventionen Schnittstelle davon aus, dass die Output-Parameter bei nullified sind.  Mit Ausnahme der explizit COM-Code werden die Formen in der folgenden Tabelle bevorzugt.  Verwenden Sie die entsprechenden COM-Formate, die aufgeführt sind für COM-Code im vorherigen Abschnitt.  
  
 **Anmerkungen und Beschreibungen**  
  
-   `_Result_nullonfailure_`  
  
     Ändert die andere Anmerkungen. Das Resultset ist null, wenn die Funktion fehlschlägt.  
  
-   `_Result_zeroonfailure_`  
  
     Ändert die andere Anmerkungen. Das Ergebnis wird auf 0 (null) festgelegt, wenn die Funktion fehlschlägt.  
  
-   `_Outptr_result_nullonfailure_`  
  
     Der zurückgegebene Zeiger verweist auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder Null, wenn die Funktion fehlschlägt. Diese Anmerkung ist für ein nicht Optionaler Parameter.  
  
-   `_Outptr_opt_result_nullonfailure_`  
  
     Der zurückgegebene Zeiger verweist auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder Null, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen optionalen Parameter.  
  
-   `_Outref_result_nullonfailure_`  
  
     Der zurückgegebene Zeiger verweist auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder Null, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen Verweisparameter.  
  
## <a name="output-reference-parameters"></a>Ausgabeverweisparameter  
 Eine häufige Verwendung der Verweisparameter ist für Output-Parameter.  Für einfache ausgabeverweisparameter – z. B. `int&`–`_Out_` korrekte Semantik bereitgestellt.  Wenn der Ausgabewert ist jedoch ein Zeiger – z. B. `int *&`– wie die entsprechende Zeiger Anmerkungen `_Outptr_ int **` nicht die richtige Semantik bereitstellen.  Die Semantik des ausgabeverweisparameter für Zeigertypen deutlicher ausgedrückt werden, verwenden Sie diese zusammengesetzten Anmerkungen:  
  
 **Anmerkungen und Beschreibungen**  
  
-   `_Outref_`  
  
     Ergebnis nach dem Status gültig sein und darf nicht null sein.  
  
-   `_Outref_result_maybenull_`  
  
     Ergebnis nach dem Status gültig sein, aber nach der Status möglicherweise null.  
  
-   `_Outref_result_buffer_(s)`  
  
     Ergebnis nach dem Status gültig sein und darf nicht null sein. Verweist auf gültige Puffer der Größe `s` Elemente.  
  
-   `_Outref_result_bytebuffer_(s)`  
  
     Ergebnis nach dem Status gültig sein und darf nicht null sein. Verweist auf gültige Puffer der Größe `s` Bytes.  
  
-   `_Outref_result_buffer_to_(s, c)`  
  
     Ergebnis nach dem Status gültig sein und darf nicht null sein. Zeigt auf Puffer der `s` Elemente, von denen das erste `c` gültig sind.  
  
-   `_Outref_result_bytebuffer_to_(s, c)`  
  
     Ergebnis nach dem Status gültig sein und darf nicht null sein. Verweist auf den Puffer von `s` Bytes, von denen das erste `c` gültig sind.  
  
-   `_Outref_result_buffer_all_(s)`  
  
     Ergebnis nach dem Status gültig sein und darf nicht null sein. Verweist auf gültige Puffer der Größe `s` gültige Elemente.  
  
-   `_Outref_result_bytebuffer_all_(s)`  
  
     Ergebnis nach dem Status gültig sein und darf nicht null sein. Verweist auf gültige Puffer `s` Bytes der gültigen Elemente.  
  
-   `_Outref_result_buffer_maybenull_(s)`  
  
     Ergebnis nach dem Status gültig sein, aber nach der Status möglicherweise null. Verweist auf gültige Puffer der Größe `s` Elemente.  
  
-   `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Ergebnis nach dem Status gültig sein, aber nach der Status möglicherweise null. Verweist auf gültige Puffer der Größe `s` Bytes.  
  
-   `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Ergebnis nach dem Status gültig sein, aber nach der Status möglicherweise null. Zeigt auf Puffer der `s` Elemente, von denen das erste `c` gültig sind.  
  
-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Ergebnis nach dem Status gültig sein, aber es kann null sein, Post-Status. Verweist auf den Puffer von `s` Bytes, von denen das erste `c` gültig sind.  
  
-   `_Outref_result_buffer_all_maybenull_(s)`  
  
     Ergebnis nach dem Status gültig sein, aber es kann null sein, Post-Status. Verweist auf gültige Puffer der Größe `s` gültige Elemente.  
  
-   `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Ergebnis nach dem Status gültig sein, aber es kann null sein, Post-Status. Verweist auf gültige Puffer `s` Bytes der gültigen Elemente.  
  
## <a name="return-values"></a>Rückgabewerte  
 Der Rückgabewert einer Funktion ähnelt einer `_Out_` Parameter ist jedoch auf einer anderen Ebene der De-reference, und Sie müssen das Konzept des Zeigers auf das Ergebnis zu berücksichtigen.  Für die folgenden Anmerkungen, ist der Rückgabewert das kommentierte Objekt – einen Skalar, ein Zeiger auf eine Struktur oder ein Zeiger auf einen Puffer. Diese Anmerkungen weisen die gleiche Semantik wie die entsprechenden `_Out_` Anmerkung.  
  
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
  
     Parameter, Felds oder Ergebnis wird im Bereich (inklusiv) von `low` zu `hi`.  Gleichbedeutend mit `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` die auf das kommentierte Objekt zusammen mit den entsprechenden Bedingungen vorab Status oder nach dem Status angewendet wird.  
  
    > [!IMPORTANT]
    >  Obwohl die Namen "in" und "out", die Semantik der enthalten `_In_` und `_Out_` müssen **nicht** gelten diese Anmerkungen.  
  
-   `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     Der kommentierte Wert `expr`.  Gleichbedeutend mit `_Satisfies_(_Curr_ == expr)` die auf das kommentierte Objekt zusammen mit den entsprechenden Bedingungen vorab Status oder nach dem Status angewendet wird.  
  
-   `_Struct_size_bytes_(size)`  
  
     Gilt für die Deklaration einer Struktur oder Klasse.  Gibt an, dass ein gültiges Objekt dieses Typs möglicherweise größer als die deklarierte Typ mit der Anzahl von Bytes wird durch `size`.  Zum Beispiel:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     Die Puffergröße in Bytes eines Parameters `pM` vom Typ `MyStruct *` wird dann ausgeführt werden:  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>Verwandte Ressourcen  
 [Code Analysis-Teamblog](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
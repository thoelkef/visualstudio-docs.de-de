---
title: "Einf&#252;hrung in SAL | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Einf&#252;hrung in SAL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Microsoft\-Quellcodeanmerkungssprache \(SAL\) stellt einen Satz Anmerkungen, die Sie verwenden können, um zu beschreiben, wie eine Funktion Parameter verwendet, Annahmen, die sie über sie macht und festgelegt, dass sie macht, wenn sie abgeschlossen.  Mit Anmerkungen werden in der Headerdatei `<sal.h>` definiert.  Visual Studio\-Codeanalyse für C\+\+ verwendet SAL\-Anmerkungen, um die Analyse von Funktionen zu ändern.  Weitere Informationen zu SAL 2,0 für Windows\-Treiberentwicklung, Sie finden [SAL 2,0 Anmerkungen für Windows\-Treiber](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 Systemintern stellen C und C\+\+ nur eingeschränkte Möglichkeiten für Entwickler von einheitlich Eilabsicht und zur Invarianz bereit.  Mithilfe SAL\-Anmerkungen verwenden, können Sie Features ausführlich beschreiben, damit Entwickler, die diese nutzen, besser verstehen, wie sie verwendet.  
  
## Was ist SAL und warum sollten Sie es verwenden?  
 Problemlos angegeben, ist SAL Dies ist eine kostengünstige Möglichkeit, den Compiler den Code für Sie überprüfen zu lassen.  
  
### SAL steigert den Wert des Codes  
 SAL kann Ihnen helfen, den Codeentwurf verständlich zu machen, Menschen und für Codeanalysetools.  Das folgende Beispiel, das C\# Laufzeitfeature `memcpy` anzeigt:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 Können mitteilen, was diese Funktion ausgeführt?  Wenn eine Funktion implementiert oder aufgerufen wird, müssen bestimmte Eigenschaften beibehalten werden, um Programmkorrektheit sicherzustellen.  Derzeit mit einer Deklaration wie im Beispiel beachten, wissen Sie nicht, was sie sind.  Ohne SAL\-Anmerkungen würden Sie auf Dokumentation erstellen oder Kommentare Code müssen.  Dies ist, was der MSDN\-Dokumentation für `memcpy` besagt:  
  
> "Kopienzählbytes src zu DEST.Wenn die Quelle und Ziel überschneiden, wird das Verhalten von memcpy undefiniert.Verwendung memmove, um von überlappenden Bereiche zu behandeln.  
> **Sicherheitshinweis:** Überprüfen, ob der Zielpuffer die gleiche Größe oder das größer als Quellpuffer ist.Weitere Informationen finden Sie die Methoden von Pufferüberläufen."  
  
 Die Dokumentation enthält Informationen, die ein paar vorschlagen, dass der Code bestimmte Eigenschaften verwalten muss, um Programmkorrektheit sicherzustellen:  
  
-   `memcpy` kopiert `count` von Bytes aus dem Quellpuffer dem Zielpuffer.  
  
-   Der Zielpuffer muss wie der Quellpuffer mindestens so groß sein.  
  
 Compiler kann jedoch die Dokumentation und die Kommentare informellen nicht lesen.  Er weiß nicht, dass eine Beziehung zwischen den zwei Puffer und `count` besteht, und es kann nicht über eine Beziehung auch effektiv schätzen.  SAL konnte mehr Klarheit über die Eigenschaften und die Implementierung der Funktion bereitstellen, wie hier gezeigt:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Beachten Sie, dass diese Kennzeichnungen den Informationen in der MSDN\-Dokumentation ähneln, aber sie sind präziser und semantischer sie folgen einem Muster.  Wenn Sie diesen Code lesen, können Sie die Eigenschaften dieser Funktion schnell verstehen und wie Pufferüberlaufsicherheitsfragen vermieden werden.  Verbessern Sie sogar, die Semantik\- Muster SAL kann, die die Effizienz und die Effektivität automatisierter Codeanalysetools in der Frühphase Suche möglicher Fehler verbessern bereitstellt.  Angenommen, dass diese verwanzte Implementierung von `wmemcpy` geschrieben:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Diese Implementierung enthält ein Common aus\-durch\-ein Fehler.  Glücklicherweise geschlossen hat der Codeautor das SALZpuffergrößenanmerkungs\-\-eincodeanalysetool konnte den ein Fehler abgefangen werden, indem diese Funktion allein analysierte.  
  
### Grundlagen von SAL  
 SAL definiert vier einfache Weise Parameter, die vom Verwendungsmuster kategorisiert werden.  
  
|Kategorie \(Category\)|Parameter\-Anmerkung|**Beschreibung**|  
|----------------------------|--------------------------|----------------------|  
|**Eingabe die aufgerufene Funktion**|`_In_`|Daten werden an die aufgerufene Funktion übergeben, und werden als schreibgeschützt behandelt.|  
|**Eingabe die aufgerufene Funktion und die Ausgabe an den Aufrufer**|`_Inout_`|Verwendbare Daten werden an die Funktion übergeben und möglicherweise werden geändert.|  
|**Ausgabe dem Aufrufer**|`_Out_`|Der Aufrufer stellt nur Leerzeichen für die aufgerufene Funktion bereit, um zu schreiben.  Die aufgerufene Funktion schreibt Daten in diesen Speicher.|  
|**Ausgabe des Zeigers auf Aufrufer**|`_Outptr_`|Wie **Ausgabe an Aufrufer**.  Der Wert, der von der aufgerufenen Funktion zurückgegeben wird, ist ein Zeiger.|  
  
 Diese vier grundlegenden Anmerkungen können expliziter gemacht werden auf unterschiedliche Weise.  Standardmäßig Zeiger muss mit Anmerkungen, den Parameter angewendet werden, um REQUIRED\-sie sein, ungleich null sein, damit die Funktion folgt.  Die am verwendetste Variante der grundlegenden Anmerkungen gibt an, dass ein Zeiger, den Parameter, OPTIONAL\-wenn er NULL ist, die Funktion ist, noch ausführen kann, mit, seine Arbeit erledigt.  
  
 Diese Tabelle zeigt, wie zwischen den erforderlichen und optionalen Parametern aufgeführt:  
  
||Parameter sind erforderlich|Parameter sind optional|  
|-|---------------------------------|-----------------------------|  
|**Eingabe die aufgerufene Funktion**|`_In_`|`_In_opt_`|  
|**Eingabe die aufgerufene Funktion und die Ausgabe an den Aufrufer**|`_Inout_`|`_Inout_opt_`|  
|**Ausgabe dem Aufrufer**|`_Out_`|`_Out_opt_`|  
|**Ausgabe des Zeigers auf Aufrufer**|`_Outptr_`|`_Outptr_opt_`|  
  
 Diese Anmerkungen unterstützen, die nicht initialisierte Werte und ungültige NULL\-Zeiger\-Verwendung in einer formalen und präzise Weise zu identifizieren.  Das Übergeben von Null zu einem erforderlichen Parameter kann zu einem Absturz, oder sie kann "Links" den Fehlercode, zurückgegeben werden.  Jede Methode, die Funktion kann nicht erfolgreich, mit, seine Arbeit erledigt.  
  
## Beispiele zu SAL  
 Dieser Abschnitt enthält Codebeispiele für die grundlegenden SAL\-Anmerkungen an.  
  
### Suchen von Fehlern mit den Visual Studio\-Codeanalysetools  
 In den Beispielen ist das Visual Studio\-Codeanalysetool zusammen mit SAL\-Anmerkungen verwendet, um Codefehler zu suchen.  Im Folgenden wird gezeigt, wie Sie dies erreichen können.  
  
##### So verwenden Sie Visual Studio\-Codeanalysetools und SAL  
  
1.  In Visual Studio ein C\+\+\-Projekt, die SAL\-Anmerkungen enthält.  
  
2.  Wählen Sie in der Menüleiste **Codeanalyse für Lösung ausführen**, **Erstellen** aus.  
  
     Betrachten Sie das \_In\_ Beispiel in diesem Abschnitt.  Wenn Sie die Codeanalyse für den Computer ausführen, wird die Warnung angezeigt:  
  
    > **Ungültiger Parameterwert C6387**   
    > "halb beliebigen" konnte "0 " sein: Dies entspricht nicht der Funktionsspezifikation für die Funktion "InCallee".  
  
### Beispiel: Die Anmerkung "\_In\_"  
 Die Anmerkung gibt die `_In_` an:  
  
-   Der Parameter muss gültig sein und nicht geändert werden.  
  
-   Die Funktion liest nur aus dem Puffer mit einem Element.  
  
-   Der Aufrufer muss den Puffer bereitstellen und initialisieren ihn.  
  
-   `_In_` gibt "schreibgeschützt" an.  Ein häufiger Fehler ist, `_In_` auf einen Parameter angewendet, der die `_Inout_` stattdessen Anmerkung haben soll.  
  
-   `_In_` zulässig, aber ignoriert durch den Analyzer auf NichtZeigerskalaren.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Wenn Sie Visual Studio\-Codeanalyse auf diesem Beispiel verwenden, überprüft er, dass die Aufrufer einen Nicht\-NULL\-Zeiger einem initialisierten Puffer für `pInt` übergeben.  In diesem Fall kann `pInt` Zeiger nicht NULL sein.  
  
### Beispiel: Die Anmerkung "\_In\_opt\_"  
 `_In_opt_` entspricht `_In_`, außer dass dem Eingabeparameter wird ermöglicht, NULL sein und daher sollte die Funktion für dies überprüfen.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Visual Studio\-Codeanalyse überprüft dass die Funktionsüberprüfungen für NULL, bevor sie auf den Puffer zugreift.  
  
### Beispiel: Die Anmerkung "\_Out\_"  
 `_Out_` unterstützt in dem ein allgemeines Szenario ein Nicht\-NULL\-Zeiger, der auf einem Elementpuffer zeigt, wird in die Funktion übergeben und initialisiert das Element.  Der Aufrufer muss den Puffer nicht vor dem Aufruf initialisieren; die aufgerufene Funktion zusichert, es zu initialisieren, bevor eine Rückgabe erfolgt.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Visual Studio\-Codeanalyse\-Tool überprüft, ob der Aufrufer einen Nicht\-NULL\-Zeiger auf einen Puffer von `pInt` werden und dass der Puffer von der Funktion initialisiert wird, bevor er beendet wird.  
  
### Beispiel: Die Anmerkung "\_Out\_opt\_"  
 `_Out_opt_` entspricht `_Out_`, außer dass der Parameter ist zulässig, dass NULL sein und daher sollte die Funktion für dies überprüfen.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio\-Codeanalyse überprüft dass dieses Funktionsüberprüfungen für NULL, bevor `pInt` dereferenziert wird, und wenn `pInt` nicht NULL ist, der Puffer von der Funktion initialisiert wird, bevor er beendet wird.  
  
### Beispiel: Die Anmerkung "\_Inout\_"  
 `_Inout_` wird verwendet, um einen Zeigerparameter Kommentieren, die möglicherweise von der Funktion geändert wird.  Der Zeiger muss auf gültigen initialisierten Daten vor dem Aufruf werden, und wenn es geändert wird, muss es einen gültigen Wert bei Rückgabe noch haben.  Die Anmerkung gibt an, dass die Funktion möglicherweise freigegeben Lesen aus und zum Einelementpuffer schreibt.  Der Aufrufer muss den Puffer bereitstellen und initialisieren ihn.  
  
> [!NOTE]
>  Wie `_Out_` muss `_Inout_` auf einen änderbaren Wert gelten.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 Visual Studio\-Codeanalyse überprüft, dass Aufrufer einen Nicht\-NULL\-Zeiger einem initialisierten Puffer für `pInt` übergeben und dass, vor Rückgabe, `pInt` noch NULL ist, der Puffer und initialisiert wird.  
  
### Beispiel: Die Anmerkung "\_Inout\_opt\_"  
 `_Inout_opt_` entspricht `_Inout_`, außer dass dem Eingabeparameter wird ermöglicht, NULL sein und daher sollte die Funktion für dies überprüfen.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio\-Codeanalyse überprüft dass dieses Funktionsüberprüfungen für NULL, bevor sie auf den Puffer zugreift, und wenn `pInt` nicht NULL ist, dass die Puffer von der Funktion initialisiert wird, bevor er beendet wird.  
  
### Beispiel: Die Anmerkung "\_Outptr\_"  
 `_Outptr_` wird verwendet, um einem Parameter Anmerkungen hinzuzufügen, der bestimmt wird, um einen Zeiger zurückgibt.  Der Parameter selbst darf nicht NULL und gibt der aufgerufenen Funktion sein ein Nicht\-NULL\-Zeiger dafür und Punkte dieses Zeigers auf initialisierten Daten.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Visual Studio\-Codeanalyse überprüft, ob der Aufrufer einen Nicht\-NULL\-Zeiger für `*pInt` führt und der Puffer von der Funktion initialisiert wird, bevor er beendet wird.  
  
### Beispiel: Die Anmerkung "\_Outptr\_opt\_"  
 `_Outptr_opt_` entspricht `_Outptr_`, außer dass der Parameter ist OPTIONAL\-\-daufrufer kann in einen NULL\-Zeiger für den Parameter übergeben.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Visual Studio\-Codeanalyse überprüft dass dieses Funktionsüberprüfungen für NULL, bevor `*pInt` dereferenziert wird, und dass der Puffer von der Funktion initialisiert wird, bevor er beendet wird.  
  
### Beispiel: Die Anmerkung "\_Success\_" in Verbindung mit "\_Out\_"  
 Anmerkungen können für die meisten Objekte angewendet werden.  Insbesondere können Sie eine ganze Funktion kommentieren.  Eine der diese Eigenschaften einer Funktion ist, dass sie folgen oder fehlschlagen kann.  Aber wie die Zuordnung zwischen einem Puffer und seine Größe, kann Funktionserfolg C\/C\+\+ oder Fehler ausdrücken.  Wie mit der `_Success_` \- Anmerkung verwenden, können Sie sagen, welcher den Erfolg für eine Funktion angezeigt.  Der Parameter der `_Success_` \- Anmerkung ist derzeit ein Ausdruck, der angibt, wenn sie zutrifft, dass die Funktion erfolgreich ausgeführt wurde.  Der Ausdruck kann beliebiger Wert sein, den der Anmerkungsparser behandeln kann.  Die Auswirkungen der Anmerkungen, nachdem die Funktion nur anwendbar sind, wenn die Funktion folgt.  Dieses Beispiel zeigt, wie `_Success_` auf `_Out_` interagiert, um genau richtig verwendet.  Sie können das Schlüsselwort `return` verwenden, um den Rückgabewert darzustellen.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 Die `_Out_` Anmerkung wird Visual Studio\-Codeanalyse, um zu überprüfen, ob der Aufrufer einen Nicht\-NULL\-Zeiger auf einen Puffer von `pInt` werden und dass der Puffer von der Funktion initialisiert wird, bevor er beendet wird.  
  
## Bewährte Methoden für SAL  
  
### Hinzufügen von Anmerkungen zu vorhandenem Code  
 SAL ist eine leistungsstarke Technologie, die Ihnen helfen kann, die Sicherheit und Zuverlässigkeit des Codes zu verbessern.  Nachdem Sie SAL erfahren, können Sie die neue Fähigkeit zu der täglichen Arbeit übernehmen.  Im neuen Code können Sie Salz\-basierte Spezifikation entwurfsbedingt verwenden gründlich; im älteren Code können Sie Anmerkungen inkrementell hinzufügen und Vorteile steigern, wenn Sie aktualisieren.  
  
 Öffentliche Header Microsoft werden bereits gekennzeichnet.  Daher schlagen Sie vor, dass in Ihren Projekten Sie zuerst Endknotenfunktionen und kommentieren Funktionen, die von Win32 APIs aufrufen, um den meisten Vorteil abzurufen.  
  
### Wann sollte ich Anmerkungen einfügen?  
 Im Folgenden einige Richtlinien:  
  
-   Kommentieren Sie alle Zeigerparameter.  
  
-   Kommentieren Sie WertBereichsanmerkungen, damit die Codeanalyse Puffer\- und Zeigersicherheit sicherstellen kann.  
  
-   Kommentieren Sie Sperrenregeln und Sperrennebeneffekte.  Weitere Informationen finden Sie unter [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md).  
  
-   Kommentieren Sie Treibereigenschaften und domänenspezifische andere Eigenschaften.  
  
 Alternativ können Sie alle Parameter mit Anmerkungen ausstatten, um den Absichtfreien verständlich Stelle zu machen und diesen zu erleichtern, zu überprüfen, ob Anmerkungen Vergangenheit wurden.  
  
## Verwandte Ressourcen  
 [Codeanalyse\-Team\-Blog](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## Siehe auch  
 [Verwenden von SAL\-Anmerkungen zum Reduzieren von C\/C\+\+\-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
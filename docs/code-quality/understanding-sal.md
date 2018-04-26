---
title: Einführung in SAL
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 82d6719ee57000ebec8ad88a90543031e0d3eeb8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="understanding-sal"></a>Einführung in SAL
Die Microsoft Source Code Annotation Language (SAL) bietet eine Reihe von Anmerkungen, die Sie verwenden können, um beschreiben, wie eine Funktion verwendet, die zugehörigen Parameter, die Annahmen, die über diese vereinfacht und die Garantien, die sie nach dem Abschluss vereinfacht. Die Anmerkungen werden in der Headerdatei definiert `<sal.h>`. Visual Studio-Codeanalyse für C++ verwendet SAL-Anmerkungen, um die Analyse der Funktionen ändern. Weitere Informationen zu SAL 2.0 für die Entwicklung von Windows-Treiber, finden Sie unter [SAL 2.0 Anmerkungen für Windows-Treiber](http://go.microsoft.com/fwlink/?LinkId=250979).

 Systemintern, geben Sie in C und C++ nur eingeschränkte Möglichkeiten für Entwickler, die konsistent Absicht und Invarianz express. Verwenden von SAL-Anmerkungen, können Sie Funktionen ausführlich beschreiben, damit Entwickler, die sie in Anspruch genommen ihre Verwendung besser verstehen können.

## <a name="what-is-sal-and-why-should-you-use-it"></a>Was ist SAL und warum sollten Sie es verwenden?
 Einfach ausgedrückt ist SAL eine kostengünstige Möglichkeit, die den Compiler Code für Sie überprüfen können.

### <a name="sal-makes-code-more-valuable"></a>SAL steigert den Wert des Codes
 SAL helfen Ihnen die Entwurfs Code leichter verständlich für Menschen und Codeanalysetools zu machen. Betrachten Sie dieses Beispiel, die die C-Laufzeit-Funktion zeigt `memcpy`:

```cpp

void * memcpy(
   void *dest,
   const void *src,
   size_t count
);

```

 Können Sie feststellen, was bewirkt, dass diese Funktion? Wenn eine Funktion implementiert oder aufgerufen wird, müssen bestimmte Eigenschaften verwaltet werden, um sicherzustellen, dass Programms auf Richtigkeit. Sie nur eine Deklaration wie im Beispiel wird ansehen, jedoch nicht erkennen, was sind. Ohne SAL-Anmerkungen müssten Sie Dokumentation oder in den Kommentaren im Code abhängig. Hier wird die MSDN-Dokumentation für `memcpy` besagt:

> "Kopien Anzahl Bytes von Src an das Ziel. Wenn sich Quelle und Ziel überlappen, ist das Verhalten des Memcpy nicht definiert. Verwenden Sie Memmove, um überlappende Bereiche zu behandeln.
> **Sicherheitshinweis:** stellen Sie sicher, dass der Zielpuffer identisch ist, Größe oder größer als der Quellpuffer. Weitere Informationen finden Sie unter Vermeiden von Pufferüberläufen."

 Die Dokumentation enthält eine Reihe von Bits von Informationen, die vor, dass der Code hat bestimmte Eigenschaften, um die Richtigkeit der Anwendung stellen Sie sicher zu verwalten:

-   `memcpy` kopiert die `count` von Bytes aus dem Quellpuffer in den Zielpuffer.

-   Der Zielpuffer muss mindestens so groß wie der Quellpuffer.

 Der Compiler kann nicht jedoch der Dokumentation oder der informelle Kommentare gelesen werden. Es ist nicht bekannt, dass eine Beziehung zwischen den zwei Puffern besteht und `count`, und es auch kann nicht effektiv zu erraten, über eine Beziehung. SAL kann weitere Klarheit über die Eigenschaften und die Implementierung der Funktion bereitstellen, wie hier gezeigt:

```cpp

void * memcpy(
   _Out_writes_bytes_all_(count) void *dest,
   _In_reads_bytes_(count) const void *src,
   size_t count
);
```

 Beachten Sie, dass diese Anmerkungen den Informationen in der MSDN-Dokumentation ähneln, aber sie präziser sind und sie eine semantische Muster entsprechen. Wenn Sie diesen Code lesen, können Sie die Eigenschaften dieser Funktion und wie Sie Puffer vor Pufferüberlauf Sicherheitsprobleme vermeiden schnell verstehen. Besser noch, können die semantische Muster, die SAL stellt der Effizienz und Effektivität des automatisierten Codeanalysetools die frühe Erkennung von potenziellen Fehlern verbessern. Stellen Sie sich vor, dass jemand diese fehlerhafte Implementierung schreibt `wmemcpy`:

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

 Diese Implementierung enthält einen allgemeine Deaktivieren von-1-Fehler. Glücklicherweise enthalten der Code Autor SAL-Anmerkung für die Puffer Größe – ein Codeanalysetool konnte den Fehler abfängt, indem Sie diese Funktion allein analysieren.

### <a name="sal-basics"></a>Grundlagen von SAL
 SAL definiert vier grundlegende Arten von Parametern, die vom Nutzungsmuster kategorisiert werden.

|Kategorie|Parameteranmerkung|Beschreibung|
|--------------|--------------------------|-----------------|
|**Eingabe für die Funktion aufgerufen.**|`_In_`|Daten, die an die aufgerufene Funktion übergeben werden und als schreibgeschützt behandelt werden.|
|**Eingabe für die Funktion aufgerufen und an den Aufrufer ausgeben**|`_Inout_`|Nutzbare Daten an die Funktion übergeben werden, und möglicherweise geändert werden.|
|**Ausgabe an den Aufrufer**|`_Out_`|Der Aufrufer dient nur zum Schreiben in die aufgerufene Funktion. Die aufgerufene Funktion schreibt Daten in diesen Speicherplatz.|
|**Ausgabe des Zeigers für Aufrufer**|`_Outptr_`|Wie **Ausgabe an den Aufrufer**. Der Wert, der von der aufgerufenen Funktion zurückgegeben wird, ist ein Zeiger.|

 Diese vier grundlegenden Anmerkungen können auf verschiedene Arten expliziter vorgenommen werden. Standardmäßig mit Anmerkungen Zeigerparametern wird angenommen, dass erforderlich – sie dürfen nicht NULL sein für die Funktion erfolgreich ausgeführt werden kann. Die am häufigsten verwendete Variation des grundlegenden Anmerkungen gibt an, dass ein Zeigerparameter optional ist, wenn er NULL ist, kann die Funktion weiterhin auf diese Weise seine Arbeitsstatus erfolgreich.

 Diese Tabelle zeigt, wie erforderlichen und optionalen Parameter unterscheiden:

||Die Parameter sind erforderlich|Parameter sind optional|
|-|-----------------------------|-----------------------------|
|**Eingabe für die Funktion aufgerufen.**|`_In_`|`_In_opt_`|
|**Eingabe für die Funktion aufgerufen und an den Aufrufer ausgeben**|`_Inout_`|`_Inout_opt_`|
|**Ausgabe an den Aufrufer**|`_Out_`|`_Out_opt_`|
|**Ausgabe des Zeigers für Aufrufer**|`_Outptr_`|`_Outptr_opt_`|

 Diese Anmerkungen Identifizierung möglicher nicht initialisierte Werte und Ungültiger null-Zeiger auf eine formale, genaue Weise verwendet. Übergeben NULL an einen erforderlichen Parameter möglicherweise verursacht einen Absturz, oder es treten einen "Fehler" Fehlercode zurückgegeben werden. In beiden Fällen kann nicht die Funktion erfolgreich ausgeführt werden, in dessen Auftrag ausführen.

## <a name="sal-examples"></a>Beispiele zu SAL
 In diesem Abschnitt sind Codebeispiele für die grundlegende SAL-Anmerkungen aufgeführt.

### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Suchen von Fehlern mit den Visual Studio Codeanalysetools
 In den Beispielen wird der Codeanalyse von Visual Studio-Tools zusammen mit SAL-Anmerkungen verwendet, um Codefehler zu suchen. Im folgenden wird erläutert, wie ein.

##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>So verwenden Sie Visual Studio-Codeanalysetools und SAL

1.  Öffnen Sie in Visual Studio ein C++-Projekt, SAL-Anmerkungen enthält.

2.  Wählen Sie in der Menüleiste **erstellen**, **Codeanalyse für Lösung ausführen**.

     Betrachten Sie die _In\_ Beispiel in diesem Abschnitt. Wenn Sie die Codeanalyse darauf ausführen, wird diese Warnung angezeigt:

    > **Ungültiger Parameterwert C6387** "anheften" '0' werden konnte: Dies entspricht nicht der Spezifikation für die Funktion "InCallee".

### <a name="example-the-in-annotation"></a>Beispiel: Die _In\_ Anmerkung
 Die `_In_` Anmerkung gibt an, dass:

-   Der Parameter muss gültig sein und wird nicht geändert werden.

-   Die Funktion liest nur aus dem Einzelelement-Puffer.

-   Der Aufrufer muss den Puffer bereitzustellen und initialisieren Sie es.

-   `_In_` Gibt an, "schreibgeschützt". Ein häufiger Fehler ist anzuwendende `_In_` auf einen Parameter, der die `_Inout_` Anmerkung stattdessen.

-   `_In_` ist zulässig, aber von der Analyzer auf Nichtzeiger skalare ignoriert.

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

 Wenn Sie Visual Studio-Codeanalyse in diesem Beispiel verwenden, überprüft Sie, dass der Aufrufer einen nicht-Null-Zeiger auf einen initialisierten Puffer für übergeben `pInt`. In diesem Fall `pInt` Zeiger darf nicht NULL sein.

### <a name="example-the-inopt-annotation"></a>Beispiel: Die _In_opt\_ Anmerkung
 `_In_opt_` entspricht dem `_In_`, außer dass der input-Parameter NULL sein kann und aus diesem Grund sollten die Funktion für diese überprüfen.

```cpp

void GoodInOptCallee(_In_opt_ int *pInt)
{
   if(pInt != NULL) {
      int i = *pInt;
   }
}

void BadInOptCallee(_In_opt_ int *pInt)
{
   int i = *pInt; // Dereferencing NULL pointer 'pInt'
}

void InOptCaller()
{
   int *pInt = NULL;
   GoodInOptCallee(pInt);
   BadInOptCallee(pInt);
}

```

 Visual Studio-Codeanalyse überprüft, dass die Funktion für NULL-Zeichen überprüft werden, bevor er auf den Puffer zugreift.

### <a name="example-the-out-annotation"></a>Beispiel: Die _Out\_ Anmerkung
 `_Out_` Ein häufiges Szenario, in dem ein nicht-NULL-Zeiger, der auf ein Element Puffer zeigt übergeben, und die Funktion initialisiert das Element, wird unterstützt. Der Aufrufer verfügt nicht über den Puffer vor dem Aufruf zu initialisieren; die aufgerufene Funktion verspricht initialisiert werden, bevor sie zurückgibt.

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

 Visual Studio-Codeanalysetool überprüft, dass der Aufrufer übergeben wird, einen nicht-NULL-Zeiger auf einen Puffer für `pInt` und, die der Puffer wird von der Funktion initialisiert, vor dem zurückgeben.

### <a name="example-the-outopt-annotation"></a>Beispiel: Die _Out_opt\_ Anmerkung
 `_Out_opt_` entspricht dem `_Out_`, außer dass der Parameter NULL sein kann und aus diesem Grund sollten die Funktion für diese überprüfen.

```cpp

void GoodOutOptCallee(_Out_opt_ int *pInt)
{
   if (pInt != NULL) {
      *pInt = 5;
   }
}

void BadOutOptCallee(_Out_opt_ int *pInt)
{
   *pInt = 5; // Dereferencing NULL pointer 'pInt'
}

void OutOptCaller()
{
   int *pInt = NULL;
   GoodOutOptCallee(pInt);
   BadOutOptCallee(pInt);
}

```

 Visual Studio-Codeanalyse überprüft, dass diese Funktion prüft, ob NULL vor `pInt` dereferenziert wird, und wenn `pInt` ist nicht NULL, dass der Puffer von der Funktion initialisiert wird, vor dem zurückgeben.

### <a name="example-the-inout-annotation"></a>Beispiel: Die _Inout\_ Anmerkung
 `_Inout_` wird verwendet, um einen Zeigerparameter mit einer Anmerkung versehen, der von der Funktion geändert werden kann. Der Zeiger muss auf gültige initialisierte Daten vor dem Aufruf, und auch wenn es sich ändert, dennoch muss einen gültigen Wert bei der Rückgabe. Die Anmerkung gibt an, dass die Funktion zum kann kostenlos lesen und in den Puffer einem Element schreiben. Der Aufrufer muss den Puffer bereitzustellen und initialisieren Sie es.

> [!NOTE]
>  Wie `_Out_`, `_Inout_` müssen anwenden, um einen änderbaren Wert.

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
   InOutCallee(pInt); // 'pInt' should not be NULL
}

```

 Visual Studio-Codeanalyse überprüft, dass der Aufrufer einen nicht-NULL-Zeiger auf einen initialisierten Puffer für übergeben `pInt`, und dass vor der Rückgabe `pInt` noch nicht NULL ist und der Puffer wird initialisiert.

### <a name="example-the-inoutopt-annotation"></a>Beispiel: Die _Inout_opt\_ Anmerkung
 `_Inout_opt_` entspricht dem `_Inout_`, außer dass der input-Parameter NULL sein kann und aus diesem Grund sollten die Funktion für diese überprüfen.

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
   int i = *pInt; // Dereferencing NULL pointer 'pInt'
   *pInt = 6;
}

void InOutOptCaller()
{
   int *pInt = NULL;
   GoodInOutOptCallee(pInt);
   BadInOutOptCallee(pInt);
}

```

 Visual Studio-Codeanalyse überprüft, dass diese Funktion auf NULL überprüft werden, bevor er auf den Puffer zugreift, und wenn `pInt` ist nicht NULL, dass der Puffer von der Funktion initialisiert wird, vor dem zurückgeben.

### <a name="example-the-outptr-annotation"></a>Beispiel: Die _Outptr\_ Anmerkung
 `_Outptr_` wird verwendet, um einen Parameter mit einer Anmerkung versehen, der einen Zeiger zurückgeben sollte hat.  Der Parameter selbst darf nicht NULL sein und die aufgerufene Funktion gibt einen nicht-NULL-Zeiger, und diese Zeiger verweist auf die initialisierte Daten.

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

 Visual Studio-Codeanalyse überprüft, dass der Aufrufer einen nicht-NULL-Zeiger übergeben wird, für die `*pInt`, und, die der Puffer wird von der Funktion initialisiert, vor dem zurückgeben.

### <a name="example-the-outptropt-annotation"></a>Beispiel: Die _Outptr_opt\_ Anmerkung
 `_Outptr_opt_` entspricht dem `_Outptr_`, außer dass der Parameter optional ist: der Aufrufer kann ein NULL-Zeiger für den Parameter übergeben.

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
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'
}

void OutPtrOptCaller()
{
   int **ppInt = NULL;
   GoodOutPtrOptCallee(ppInt);
   BadOutPtrOptCallee(ppInt);
}

```

 Visual Studio-Codeanalyse überprüft, dass diese Funktion prüft, ob NULL vor `*pInt` dereferenziert wird, und, die der Puffer wird von der Funktion initialisiert, vor dem zurückgeben.

### <a name="example-the-success-annotation-in-combination-with-out"></a>Beispiel: Die _Success\_ Anmerkung in Kombination mit _Out\_
 Anmerkungen können auf die meisten Objekte angewendet werden.  Insbesondere können Sie eine gesamte Funktion mit Anmerkungen versehen.  Eines der offensichtlichste Merkmale einer Funktion ist, dass es erfolgreich ausgeführt werden oder fehlschlagen kann. Aber wie die Zuordnung zwischen einen Puffer und seiner Größe, C/C++-Funktion Erfolg oder Misserfolg express kann nicht. Mithilfe der `_Success_` Anmerkung, können Sie sagen, welche Erfolg für eine Funktion aussieht.  Der Parameter für die `_Success_` Anmerkung ist nur ein Ausdruck, dass es sich bei "true" wird er gibt an, dass die Funktion erfolgreich war. Der Ausdruck kann alles sein, die die Anmerkung Parser behandeln können. Die Auswirkungen der Anmerkungen, die nach der Rückkehr der Funktion sind nur anwendbar, wenn die Funktion erfolgreich ausgeführt wird. Dieses Beispiel zeigt, wie `_Success_` interagiert mit `_Out_` an das richtige tun. Verwenden Sie das Schlüsselwort `return` zur Darstellung des Rückgabewerts.

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

 Die `_Out_` Anmerkung bewirkt, dass Visual Studio-Codeanalyse so überprüfen Sie, dass der Aufrufer übergeben wird, einen nicht-NULL-Zeiger auf einen Puffer für `pInt`, und, die der Puffer wird von der Funktion initialisiert, vor dem zurückgeben.

## <a name="sal-best-practice"></a>Bewährte Methoden für SAL

### <a name="adding-annotations-to-existing-code"></a>Hinzufügen von Anmerkungen zu vorhandenem Code
 SAL ist eine leistungsstarke Technologie, mit die Sie die Sicherheit und Zuverlässigkeit des Codes verbessern kann. Nachdem Sie SAL vertraut sind, können Sie neue Qualifikation auf Ihrer täglichen Arbeit anwenden. In neuem Code können Sie programmbedingt während des gesamten SAL-basierte Spezifikationen; in älterem Code können inkrementell Hinzufügen von Anmerkungen und damit zur Erhöhung der Vorteile der jedes Mal, wenn Sie aktualisieren.

 Öffentliche Microsoft-Header sind bereits mit Anmerkungen versehen. Aus diesem Grund wird empfohlen, in Ihren Projekten Sie zuerst mit einer Anmerkung versehen knotenfunktionen und Funktionen, die Aufrufen von Win32-APIs verwendet, um die meisten nutzen zu können.

### <a name="when-do-i-annotate"></a>Wann sollte ich Anmerkungen einfügen?
 Es folgen einige Richtlinien:

-   Kommentieren Sie alle Zeigerparameter.

-   Kommentieren Sie Wertebereich Anmerkungen, sodass Codeanalyse Puffer und Zeiger Sicherheit gewährleisten können.

-   Kommentieren Sie Sperren Regeln und Sperren Nebeneffekte. Weitere Informationen finden Sie unter [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md).

-   Kommentieren Sie die Treiber und andere domänenspezifische-Eigenschaften.

 Oder Sie können alle Parameter, um die beabsichtigte löschen im gesamten vorzunehmen und zu vereinfachen, überprüfen Sie, dass Anmerkungen geschehen mit Anmerkungen versehen.

## <a name="related-resources"></a>Verwandte Ressourcen
 [Code Analysis-Teamblog](http://go.microsoft.com/fwlink/p/?LinkId=251197)

## <a name="see-also"></a>Siehe auch
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md) [Funktionsverhalten](../code-quality/annotating-function-behavior.md) [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md) [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md) [angeben, wann und wo eine Anmerkung gültig](../code-quality/specifying-when-and-where-an-annotation-applies.md) [empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
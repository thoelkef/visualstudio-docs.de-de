---
title: Einführung in SAL
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 7f79796d186f5a365c37a8e24a3e523aba7ceb72
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55946651"
---
# <a name="understanding-sal"></a>Einführung in SAL

Die Microsoft-Quellcode Annotation Language (SAL) bietet einen Satz von Anmerkungen, die Sie zum Beschreiben, wie eine Funktion verwendet die Parameter, die Annahmen, die über diese vereinfacht und die Garantien sie gewährleistet, wenn er abgeschlossen ist, verwenden können. Die Anmerkungen werden in der Headerdatei definiert `<sal.h>`. Visual Studio-Codeanalyse für C++ wird SAL-Anmerkungen, um die Analyse von Funktionen zu ändern. Weitere Informationen zu SAL 2.0 für die Windows-Treiberentwicklung finden Sie unter [SAL 2.0 Anmerkungen für die Windows-Treiber](http://go.microsoft.com/fwlink/?LinkId=250979).

C- und C++ bieten systemintern, nur eingeschränkte Möglichkeiten für Entwickler zum Zweck und Invarianz konsistent Ausdrücken auf. Verwenden von SAL-Anmerkungen, können Sie Ihre Funktionen ausführlicher beschreiben, damit Entwickler, die sie verwendet werden wie ihre Verwendung besser verstehen können.

## <a name="what-is-sal-and-why-should-you-use-it"></a>Was ist SAL und warum sollten Sie es verwenden?

Einfach ausgedrückt ist SAL einem kostengünstigen Weg, den Compiler, die Sie Ihrem Code prüfen lassen.

### <a name="sal-makes-code-more-valuable"></a>SAL steigert den Wert des Codes

SAL können Sie Ihren Codeentwurf leichter verständlich für Menschen und Codeanalysetools treffen. Betrachten Sie Folgendes Beispiel an, die die C-Runtime-Funktion zeigt `memcpy`:

```cpp

void * memcpy(
   void *dest,
   const void *src,
   size_t count
);
```

Können Sie feststellen, was diese Funktion macht? Wenn eine Funktion implementiert oder aufgerufen wird, müssen bestimmte Eigenschaften verwaltet werden, um sicherzustellen, dass Richtigkeit des Programms. Durch das alleinige untersuchen eine Deklaration, wie im Beispiel, wissen Sie nicht genau. Ohne SAL-Anmerkungen müssten Sie die Dokumentation oder in den Kommentaren im Code verwenden. Hier ist die MSDN-Dokumentation für `memcpy` besagt:

> "Kopien Anzahl der Bytes von Src an Dest. Wenn sich Quelle und Ziel überlappen, ist das Verhalten der Memcpy nicht definiert. Verwenden Sie Memmove, um überlappende Bereiche zu behandeln.
> **Sicherheitshinweis:** Stellen Sie sicher, dass der Zielpuffer dieselbe Größe wie der Quellpuffer aufweist bzw. größer ist. Weitere Informationen finden Sie vermeiden von Pufferüberläufen."

Die Dokumentation enthält eine Reihe von Bits von Informationen, die wird empfohlen, dass der Code hat bestimmte Eigenschaften aus, um die Richtigkeit des Programms beibehalten:

- `memcpy` kopiert die `count` von Bytes aus dem Quellarray in den Zielpuffer.

- Der Zielpuffer muss mindestens so groß wie der Quellpuffer.

Der Compiler kann nicht jedoch die Dokumentation oder in informellen Kommentare lesen. Nicht, dass eine Beziehung zwischen zwei Puffern vorhanden ist, und `count`, und es auch kann nicht effektiv zu einer Beziehung. SAL kann mehr Klarheit darüber, wie die Eigenschaften und die Implementierung der Funktion bereitstellen, wie hier gezeigt:

```cpp

void * memcpy(
   _Out_writes_bytes_all_(count) void *dest,
   _In_reads_bytes_(count) const void *src,
   size_t count
);
```

Beachten Sie, dass diese Anmerkungen den Informationen in der MSDN-Dokumentation ähnelt, aber sie präziser sind und sie einen semantischen Muster folgen. Wenn Sie diesen Code lesen, können Sie die Eigenschaften dieser Funktion und wie Sie Puffer Pufferüberlauf Sicherheitsprobleme zu vermeiden schnell verstehen. Noch besser ist, können die semantische Muster, die SAL stellt die Effizienz und Effektivität der automatisierten Codeanalysetools die frühe Erkennung der potenziellen Fehlern verbessern. Stellen Sie sich vor, dass ein Benutzer diese fehlerhafte Implementierung der schreibt `wmemcpy`:

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

Diese Implementierung enthält einen häufiger Fehler der aus ein. Zum Glück enthalten der Code-Autor SAL-Anmerkung für die Puffer Größe – ein Codeanalysetool abfangen den Fehler durch diese Funktion, die allein analysieren.

### <a name="sal-basics"></a>Grundlagen von SAL
 SAL definiert vier grundlegende Arten von Parametern, die durch die Verwendungsmuster kategorisiert werden.

|Kategorie|Parameteranmerkung|Beschreibung|
|--------------|--------------------------|-----------------|
|**Eingabe für die Funktion aufgerufen.**|`_In_`|Daten, die an die aufgerufene Funktion übergeben werden und als schreibgeschützt behandelt werden.|
|**Eingabe für die Funktion aufgerufen und an Aufrufer ausgeben**|`_Inout_`|Brauchbare Daten an die Funktion übergeben werden, und möglicherweise geändert werden.|
|**Ausgabe an den Aufrufer**|`_Out_`|Der Aufrufer bietet nur Platz für die aufgerufene Funktion zu schreiben. Die aufgerufene Funktion schreibt Daten in diesen Speicherplatz.|
|**Ausgabe eines Zeigers auf den Aufrufer**|`_Outptr_`|Wie **Ausgabe an den Aufrufer**. Der Wert, der von der aufgerufenen Funktion zurückgegeben wird, ist ein Zeiger.|

 Diese vier grundlegende Anmerkungen können auf verschiedene Arten expliziter vorgenommen werden. Standardmäßig mit Anmerkungen versehene Zeigerparameter wird angenommen, dass erforderlich – sie muss ungleich NULL für die Funktion erfolgreich ausgeführt werden kann. Die am häufigsten verwendete Variation der grundlegenden Anmerkungen gibt an, dass ein Zeigerparameter optional ist, wenn er NULL ist, kann die Funktion weiterhin in die Arbeit erfolgreich.

 Diese Tabelle zeigt, wie Sie die erforderlichen und optionalen Parametern unterscheiden:

||Die Parameter sind erforderlich|Parameter sind optional|
|-|-----------------------------|-----------------------------|
|**Eingabe für die Funktion aufgerufen.**|`_In_`|`_In_opt_`|
|**Eingabe für die Funktion aufgerufen und an Aufrufer ausgeben**|`_Inout_`|`_Inout_opt_`|
|**Ausgabe an den Aufrufer**|`_Out_`|`_Out_opt_`|
|**Ausgabe eines Zeigers auf den Aufrufer**|`_Outptr_`|`_Outptr_opt_`|

 Diese Anmerkungen Identifizieren möglicher nicht initialisierte Werte und Ungültiger null-Zeiger in einer formalen und genaue Weise verwendet. Übergeben NULL an ein erforderlicher Parameter möglicherweise einen Absturz verursachen, oder es treten einen "Fehler" Fehlercode zurückgegeben werden. In beiden Fällen kann nicht die Funktion erfolgreich ausgeführt werden, auf diese Weise einschlagen.

## <a name="sal-examples"></a>Beispiele zu SAL
 Dieser Abschnitt zeigt die Codebeispiele für die grundlegende SAL-Anmerkungen.

### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Suchen von Fehlern mit den Visual Studio Codeanalysetools
 In den Beispielen wird das Tool für Visual Studio-Codeanalyse zusammen mit SAL-Anmerkungen verwendet, um Codefehler zu finden. Hier ist wie das geht.

#### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>So verwenden Sie Visual Studio-Codeanalysetools und SAL

1.  Öffnen Sie in Visual Studio ein C++-Projekt, SAL-Anmerkungen enthält.

2.  Wählen Sie auf der Menüleiste **erstellen**, **Codeanalyse für Lösung ausführen**.

     Betrachten Sie die \_In\_ Beispiel in diesem Abschnitt. Wenn Sie die Codeanalyse darauf ausführen, wird diese Warnung angezeigt:

    > **Ungültiger Parameterwert in C6387** "pInt" kann "0" sein: Dies entspricht nicht der Spezifikation für die Funktion "InCallee" Funktionsspezifikation.

### <a name="example-the-in-annotation"></a>Beispiel: Die \_In\_ Anmerkung

Die `_In_` Anmerkung gibt an, dass:

-   Der Parameter muss gültig sein und wird nicht geändert werden.

-   Die Funktion liest nur aus dem Puffer für die einzelnen Element.

-   Der Aufrufer muss den Puffer bereitstellen, und initialisieren Sie sie.

-   `_In_` Gibt an, "schreibgeschützt". Ein häufiger Fehler besteht darin, anzuwendende `_In_` auf einen Parameter, die haben, sollte die `_Inout_` Anmerkung stattdessen.

-   `_In_` kann jedoch vom Analyzer auf Nichtzeiger skalare ignoriert.

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

Wenn Sie Visual Studio-Codeanalyse in diesem Beispiel verwenden, es wird überprüft, ob der Aufrufer einen nicht-Null-Zeiger auf ein initialisiertes Puffer für übergeben `pInt`. In diesem Fall `pInt` Zeiger darf nicht NULL sein.

### <a name="example-the-inopt-annotation"></a>Beispiel: Die \_In\_opt\_ Anmerkung

`_In_opt_` entspricht dem `_In_`, außer dass input-Parameters NULL sein kann und aus diesem Grund sollten die Funktion für diese überprüfen.

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

Visual Studio-Codeanalyse überprüft, dass die Funktion auf NULL prüft, bevor er auf den Puffer zugreift.

### <a name="example-the-out-annotation"></a>Beispiel: Die \_Out\_ Anmerkung

`_Out_` Ein häufiges Szenario, in dem ein nicht-NULL-Zeiger, der auf einen Puffer Element verweist übergeben wird, und die Funktion initialisiert das Element, wird unterstützt. Initialisiert den Puffer vor dem Aufruf muss der Aufrufer keine; die aufgerufene Funktion verspricht sie zu initialisieren, bevor sie zurückkehrt.

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

Visual Studio Code Analysis Tool überprüft, dass der Aufrufer einen nicht-NULL-Zeiger auf einen Puffer für übergibt `pInt` und, die der Puffer wird von der Funktion initialisiert, vor dem zurückgeben.

### <a name="example-the-outopt-annotation"></a>Beispiel: Die \_Out\_opt\_ Anmerkung

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

Visual Studio-Codeanalyse überprüft, dass diese Funktion prüft, ob NULL vor `pInt` dereferenziert wird, und wenn `pInt` ist nicht NULL, dass der Puffer von der Funktion initialisiert wird, bevor sie zurückkehrt.

### <a name="example-the-inout-annotation"></a>Beispiel: Die \_Inout\_ Anmerkung

`_Inout_` wird verwendet, um einen Zeigerparameter zu kommentieren, der von der Funktion geändert werden kann. Der Zeiger muss auf gültige initialisierte Daten vor dem Aufruf zeigen, und auch wenn es geändert wird, noch muss einen gültigen Wert bei der Rückgabe. Die Anmerkung gibt an, dass die Funktion kann frei auslesen und in den Puffer einem Element schreiben. Der Aufrufer muss den Puffer bereitstellen, und initialisieren Sie sie.

> [!NOTE]
> Wie `_Out_`, `_Inout_` müssen auf einen änderbaren Wert anwenden.

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

Visual Studio-Codeanalyse überprüft, dass der Aufrufer einen nicht-NULL-Zeiger auf ein initialisiertes Puffer für übergeben `pInt`, und vor der Rückgabe `pInt` weiterhin ungleich NULL ist und der Puffer initialisiert wird.

### <a name="example-the-inoutopt-annotation"></a>Beispiel: Die \_Inout\_opt\_ Anmerkung

`_Inout_opt_` entspricht dem `_Inout_`, außer dass input-Parameters NULL sein kann und aus diesem Grund sollten die Funktion für diese überprüfen.

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

Visual Studio-Codeanalyse überprüft, dass diese Funktion auf NULL überprüft werden, bevor er auf den Puffer zugreift, und wenn `pInt` ist nicht NULL, dass der Puffer von der Funktion initialisiert wird, bevor sie zurückkehrt.

### <a name="example-the-outptr-annotation"></a>Beispiel: Die \_Outptr\_ Anmerkung

`_Outptr_` wird verwendet, um einen Parameter mit Anmerkungen versehen, die einen Zeiger zurückgibt.  Der Parameter selbst darf nicht NULL sein und die aufgerufene Funktion einen nicht-NULL-Zeiger zurückgegeben, es aus, und diese Zeiger verweist auf die initialisierte Daten.

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

Visual Studio-Codeanalyse überprüft, dass der Aufrufer einen nicht-NULL-Zeiger übergeben wird, für die `*pInt`, und die der Puffer wird von der Funktion initialisiert, vor dem zurückgeben.

### <a name="example-the-outptropt-annotation"></a>Beispiel: Die \_Outptr\_opt\_ Anmerkung

`_Outptr_opt_` entspricht dem `_Outptr_`, außer dass der Parameter optional ist — der Aufrufer kann ein NULL-Zeiger für den Parameter übergeben.

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

Visual Studio-Codeanalyse überprüft, dass diese Funktion prüft, ob NULL vor `*pInt` dereferenziert wird, und die der Puffer wird von der Funktion initialisiert, vor dem zurückgeben.

### <a name="example-the-success-annotation-in-combination-with-out"></a>Beispiel: Die \_Erfolg\_ Anmerkung in Kombination mit \_Out\_

Anmerkungen können auf die meisten Objekte angewendet werden.  Insbesondere können Sie eine gesamte Funktion versehen.  Eine der offensichtlichsten Eigenschaften einer Funktion ist, dass es erfolgreich ausgeführt werden oder fehlschlagen kann. Aber wie die Zuordnung zwischen einem Puffer und seiner Größe, C/C++-Funktion Erfolg oder Misserfolg express kann nicht. Mithilfe der `_Success_` Anmerkung, Sie können angeben, welche Erfolg für eine Funktion aussieht.  Der Parameter für die `_Success_` Anmerkung ist nur ein Ausdruck, wann ist "true" gibt an, dass die Funktion erfolgreich war. Der Ausdruck kann alles sein, der die Anmerkung Parser verarbeiten kann. Die Auswirkungen der Anmerkungen, nachdem die Funktion gelten nur, wenn die Funktion erfolgreich ist. Dieses Beispiel zeigt, wie `_Success_` interagiert mit `_Out_` auf das richtige tun. Sie können mithilfe des Schlüsselworts `return` zur Darstellung des zurückgegeben Wert.

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

Die `_Out_` Anmerkung bewirkt, dass Visual Studio-Codeanalyse, um zu überprüfen, dass der Aufrufer einen nicht-NULL-Zeiger auf einen Puffer für übergibt `pInt`, und die der Puffer wird von der Funktion initialisiert, vor dem zurückgeben.

## <a name="sal-best-practice"></a>Bewährte Methoden für SAL

### <a name="adding-annotations-to-existing-code"></a>Hinzufügen von Anmerkungen zu vorhandenem Code

SAL ist eine leistungsstarke Technologie, mit die Sie die Sicherheit und Zuverlässigkeit des Codes verbessern kann. Wenn Sie wissen, dass die SAL, können Sie die neue Fähigkeit für Ihre tägliche Arbeit anwenden. In neuem Code können Sie standardmäßig in der gesamten SAL-basierte Spezifikationen verwenden. in älterem Code können Sie inkrementell Hinzufügen von Anmerkungen und verbessern so die Vorteile aus, bei jeder Aktualisierung.

Öffentliche Microsoft-Header werden bereits mit Anmerkungen versehen. Aus diesem Grund wird empfohlen, dass in Ihren Projekten Sie zuerst mit Anmerkungen versehen Leaf-Knoten-Funktionen und Funktionen, die Aufrufen von Win32-APIs, um die größten Vorteile zu erhalten.

### <a name="when-do-i-annotate"></a>Wann sollte ich Anmerkungen einfügen?

Es folgen einige Richtlinien:

- Versehen Sie alle Zeigerparameter.

- Versehen Sie Wertebereich Anmerkungen, um die Codeanalyse Puffer und Zeiger-Sicherheit gewährleisten können.

- Versehen von Regeln und Sperren Nebeneffekte. Weitere Informationen finden Sie unter [Sperrverhalten kommentieren](../code-quality/annotating-locking-behavior.md).

- Kommentieren Sie Treibereigenschaften und andere domänenspezifische-Eigenschaften.

Oder Sie können alle Parameter, die Ihre beabsichtigte löschen während des gesamten vornehmen und zu vereinfachen, um zu überprüfen, dass Anmerkungen ausgeführt wird, mit Anmerkungen versehen.

## <a name="related-resources"></a>Verwandte Ressourcen

[Code Analysis-Teamblog](http://go.microsoft.com/fwlink/p/?LinkId=251197)

## <a name="see-also"></a>Siehe auch

- [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)
- [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)
- [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)
- [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)
- [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
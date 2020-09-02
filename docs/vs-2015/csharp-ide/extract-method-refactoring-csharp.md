---
title: Refactoring zum Extrahieren von Methoden (c#) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e6d5e7913a7433fd4b30da490f33dd614c3e2b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667543"
---
# <a name="extract-method-refactoring-c"></a>Umgestaltung "Methode extrahieren" (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Extract Method** ist ein Refactoring-Vorgang, der eine einfache Möglichkeit zum Erstellen einer neuen Methode aus einem Code Fragment in einem vorhandenen Member bietet.

 Mithilfe der **Methode extrahieren**können Sie eine neue Methode erstellen, indem Sie eine Auswahl von Code aus dem Codeblock eines vorhandenen Members extrahieren. Die neue, extrahierte Methode enthält den ausgewählten Code, und der ausgewählte Code im vorhandenen Member wird durch einen-Rückruf der neuen Methode ersetzt. Wenn Sie ein Code Fragment in eine eigene Methode setzen, können Sie Code schnell und präzise neu organisieren, um die Wiederverwendung und Lesbarkeit zu verbessern.

 Die **Extract-Methode** bietet die folgenden Vorteile:

- Fördert bewährte Programmiermethoden, indem diskrete, wiederverwendbare Methoden hervorgehoben werden.

- Fördert selbst dokumentierenden Code durch eine gute Organisation.

     Wenn beschreibende Namen verwendet werden, können Methoden auf hoher Ebene eher wie eine Reihe von Kommentaren gelesen werden.

- Fördert die Erstellung differenziertere Methoden, um das Überschreiben zu vereinfachen.

- Verringert die Code Duplizierung.

### <a name="to-use-extract-method"></a>So verwenden Sie die Extract-Methode

1. Erstellen Sie eine Konsolenanwendung mit dem Namen `ExtractMethod`, und ersetzen Sie `Program` durch den folgenden Beispielcode.

    ```csharp
    class A
    {
        const double PI = 3.141592;

        double CalculatePaintNeeded(double paintPerUnit, double radius)
        {
            // Select any of the following:
            // 1. The entire next line of code.
            // 2. The right-hand side of the next line of code.
            // 3. Just "PI *" of the right-hand side of the next line
            //    of code (to see the prompt for selection expansion).
            // 4.  All code within the method body.
            // ...Then invoke Extract Method.

            double area = PI * radius * radius;

            return area / paintPerUnit;
        }
    }
    ```

2. Wählen Sie das zu extrahierende Code Fragment aus:

    ```csharp
    double area = PI * radius * radius;
    ```

3. Klicken Sie im Menü **umgestalten** auf **Methode extrahieren**.

     Das Dialogfeld **Methode extrahieren** wird angezeigt.

     Alternativ können Sie auch die Tastenkombination STRG + R, M eingeben, um das Dialogfeld **Methode extrahieren** anzuzeigen.

     Sie können auch mit der rechten Maustaste auf den ausgewählten Code klicken, auf **umgestalten**zeigen und dann auf **Methode extrahieren** klicken, um das Dialogfeld **Methode extrahieren** anzuzeigen.

4. Geben Sie `CircleArea` im Feld **Neuer Methodenname** einen Namen für die neue Methode an, z. b..

     Eine Vorschau der neuen Methoden Signatur wird unter **Vorschau der Methoden Signatur**angezeigt.

5. Klicken Sie auf **OK**.

## <a name="remarks"></a>Bemerkungen
 Wenn Sie den **extract-Methoden** Befehl verwenden, wird die neue-Methode nach dem Quellmember in derselben Klasse eingefügt.

## <a name="partial-types"></a>Partielle Typen
 Wenn es sich bei der Klasse um einen partiellen Typ handelt, generiert die **Extract-Methode** die neue Methode direkt nach dem Quellmember. **Extract Method** bestimmt die Signatur der neuen Methode und erstellt eine statische Methode, wenn vom Code in der neuen Methode auf keine Instanzdaten verwiesen wird.

## <a name="generic-type-parameters"></a>Generische Typparameter
 Wenn Sie eine Methode extrahieren, die einen nicht eingeschränkten generischen Typparameter aufweist, fügt der generierte Code diesen Parameter nur dann den `ref` Modifizierer hinzu, wenn ihm ein Wert zugewiesen wird. Wenn die extrahierte Methode Verweis Typen als generisches Typargument unterstützt, sollten Sie den- `ref` Modifizierer manuell dem-Parameter in der Methoden Signatur hinzufügen.

## <a name="anonymous-methods"></a>Anonyme Methoden
 Wenn Sie versuchen, einen Teil einer anonymen Methode zu extrahieren, der einen Verweis auf eine lokale Variable enthält, die entweder deklariert oder außerhalb der anonymen Methode referenziert wird, werden Sie von Visual Studio vor möglichen semantischen Änderungen gewarnt.

 Wenn eine anonyme Methode den Wert einer lokalen Variablen verwendet, wird der Wert zu dem Zeitpunkt abgerufen, an dem die anonyme Methode ausgeführt wird. Wenn eine anonyme Methode in eine andere Methode extrahiert wird, wird der Wert der lokalen Variablen zum Zeitpunkt des Aufrufes der extrahierten Methode abgerufen.

 Diese semantische Änderung wird im folgenden Beispiel veranschaulicht. Wenn dieser Code ausgeführt wird, wird **11** in der Konsole gedruckt. Wenn Sie die **Extract-Methode** verwenden, um den Code Bereich zu extrahieren, der durch Code Kommentare als eigene Methode gekennzeichnet ist, und dann den umgestalteten Code auszuführen, wird **10** in der Konsole gedruckt.

```csharp
class Program
{
    delegate void D();
    D d;
    static void Main(string[] args)
    {
        Program p = new Program();
        int i = 10;
        /*begin extraction*/
            p.d = delegate { Console.WriteLine(i++); };
        /*end extraction*/
        i++;
        p.d();
    }
}
```

 Um diese Situation zu umgehen, erstellen Sie die lokalen Variablen, die in den Feldern der anonymen Methode der-Klasse verwendet werden.

## <a name="see-also"></a>Weitere Informationen
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)
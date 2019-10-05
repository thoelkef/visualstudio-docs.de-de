---
title: Extrahovat Metodu Refactoring (c#) | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5a889250e641e004bdb0d89f6965c43c3d6b8e2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155258"
---
# <a name="extract-method-refactoring-c"></a>Umgestaltung "Methode extrahieren" (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Methode extrahieren** ist ein Umgestaltungsvorgang, die eine einfache Möglichkeit zum Erstellen einer neuen Methode aus einem Codefragment in einem vorhandenen Member bereitstellt.  
  
 Mithilfe von **Methode extrahieren**, Sie können eine neue Methode erstellen, indem Sie eine Auswahl von Code innerhalb des Codeblocks, der einen vorhandenen Member extrahieren. Die neue, extrahierte Methode enthält des ausgewählten Codes, und der ausgewählte Code in das vorhandene Element mit einem Aufruf in die neue Methode ersetzt wird. Ein Fragment des Codes in eine eigene Methode umwandeln können Sie schnell und präzise Code für eine bessere Wiederverwendung und Lesbarkeit neu zu organisieren.  
  
 **Methode extrahieren** hat die folgenden Vorteile:  
  
- Ermutigt bewährten Programmiermethoden, indem diskret, wieder verwendbaren Methoden hervorgehoben.  
  
- Ermutigt Dokumentieren von Code über die Struktur selbst.  
  
     Erfahren Sie mehr kann beschreibende Namen verwendet wird, allgemeine Methoden sind eine Reihe von Kommentaren wie.  
  
- Ermöglicht die Erstellung von differenziertere Methoden zur Vereinfachung der überschreiben.  
  
- Reduziert die Duplizierung von Code.  
  
### <a name="to-use-extract-method"></a>Verwenden der Methode extrahieren  
  
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
  
2. Wählen Sie das Codefragment, die, das Sie extrahieren möchten:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3. Auf der **Umgestalten** Menü klicken Sie auf **Methode extrahieren**.  
  
     Die **Methode extrahieren** Dialogfeld wird angezeigt.  
  
     Alternativ können Sie auch die Tastenkombination STRG + R, M anzuzeigende eingeben der **Methode extrahieren** Dialogfeld.  
  
     Sie können auch mit der rechten Maustaste den ausgewählten code, zeigen Sie auf **Umgestalten**, und klicken Sie dann auf **Methode extrahieren** zum Anzeigen der **Methode extrahieren** Dialogfeld.  
  
4. Geben Sie einen Namen für die neue Methode, wie z. B. `CircleArea`in die **Neuer Methodenname** Feld.  
  
     Eine Vorschau auf die neue Methodensignatur zeigt unter **Vorschau der Methodensignatur**.  
  
5. Klicken Sie auf **OK**.  
  
## <a name="remarks"></a>Hinweise  
 Bei Verwendung der **Methode extrahieren** können die neue Methode ist die Quelle Element in der gleichen Klasse eingefügt.  
  
## <a name="partial-types"></a>Partielle Typen  
 Wenn die Klasse ein partieller Typ ist, dann ist **Methode extrahieren** generiert die neue Methode, die unmittelbar nach der Quellmember. **Methode extrahieren** bestimmt die Signatur der neuen Methode und erstellt eine statische Methode, wenn keine Instanzdaten durch den Code in die neue Methode verwiesen werden.  
  
## <a name="generic-type-parameters"></a>Generische Typparameter  
 Wenn Sie eine Methode, die einen uneingeschränkte generischen Typparameter verfügt extrahieren, wird der generierte Code nicht hinzufügen der `ref` Modifizierer, um diesen Parameter, wenn ein Wert zugewiesen wird. Wenn die extrahierte Methode wird als das generische Typargument Verweistypen unterstützt, sollten Sie manuell hinzufügen der `ref` Modifizierer, um den Parameter in der Methodensignatur.  
  
## <a name="anonymous-methods"></a>Anonyme Methoden  
 Wenn Sie versuchen, die Teil einer anonymen Methode extrahieren, die einen Verweis auf eine lokale Variable enthält, die deklariert bzw. außerhalb der anonymen Methode verwiesen wird, klicken Sie dann warnt Visual Studio Sie, zur semantischen Änderungen.  
  
 Wenn eine anonyme Methode den Wert einer lokalen Variablen verwendet wird, wird der Wert im Moment abgerufen, die die anonyme Methode ausgeführt wird. Wenn eine anonyme Methode in einer anderen Methode extrahiert werden, wird der Wert der lokalen Variablen zum Zeitpunkt des Aufrufs an die extrahierte Methode abgerufen.  
  
 Das folgende Beispiel veranschaulicht diese semantische Änderungen. Wenn dieser Code, klicken Sie dann ausgeführt wird **11** wird in der Konsole ausgegeben werden. Bei Verwendung von **Methode extrahieren** extrahieren die Region des Codes, der durch die Codekommentare in eine eigene Methode markiert ist, und führen Sie dann die umgestalteten Code, klicken Sie dann **10** wird in der Konsole ausgegeben werden.  
  
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
  
 Um diese Situation zu umgehen, stellen Sie die lokalen Variablen, die die anonyme Methode Felder der Klasse verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)
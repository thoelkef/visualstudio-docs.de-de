---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-method
title: Umgestaltung (c#) Methode extrahieren | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 18fc4c20b39341f884fb23b51822ce7f6e427007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="extract-method-refactoring-c"></a>Umgestaltung "Methode extrahieren" (C#)
**Methode extrahieren** ist ein Umgestaltungsvorgang, können eine einfache Möglichkeit, eine neue Methode aus einem Codefragment in einem vorhandenen Member zu erstellen.  
  
 Mit **Methode extrahieren**, erstellen Sie eine neue Methode, mit dem eine Auswahl von Code aus innerhalb eines vorhandenen Mitglieds der Codeblock zu extrahieren. Die neue, extrahierte Methode enthält den ausgewählten Code, und der ausgewählte Code in das vorhandene Element mit einem Aufruf in die neue Methode ersetzt wird. Aktivieren ein Fragment des Codes in eine eigene Methode können Sie schnell und präzise reorganize Code zur Wiederverwendung und die Lesbarkeit besser.  
  
 **Methode extrahieren** hat die folgenden Vorteile:  
  
-   Betonung von diskreten, wiederverwendbare-Methoden, um am besten Codierungstechniken vertraut zu machen.  
  
-   Sich selbst dokumentierender Code durch gute Organisation vertraut zu machen.  
  
     Wenn aussagekräftige Namen verwendet wird, sind allgemeine Methoden sind können weitere, z. B. eine Reihe von Kommentaren.  
  
-   Vertraut zu machen, die Erstellung von differenziertere Methoden zum Überschreiben zu vereinfachen.  
  
-   Codeduplikaten wird reduziert.  
  
### <a name="to-use-extract-method"></a>Verwenden der Methode extrahieren  
  
1.  Erstellen Sie eine Konsolenanwendung mit dem Namen `ExtractMethod`, und ersetzen Sie `Program` durch den folgenden Beispielcode.  
  
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
  
2.  Wählen Sie das Codefragment, die, das Sie extrahieren möchten:  
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  Auf der **Umgestalten** Menü klicken Sie auf **Methode extrahieren**.  
  
     Die **Methode extrahieren** Dialogfeld wird angezeigt.  
  
     Alternativ können Sie auch die Tastenkombination STRG + R, M anzuzeigenden eingeben der **Methode extrahieren** (Dialogfeld).  
  
     Sie können auch mit der rechten Maustaste den ausgewählten code, zeigen Sie auf **Umgestalten**, und klicken Sie dann auf **Methode extrahieren** zum Anzeigen der **Methode extrahieren** (Dialogfeld).  
  
4.  Geben Sie einen Namen für die neue Methode, wie z. B. `CircleArea`in der **neue Methodennamen** Feld.  
  
     Eine Vorschau der neuen Methodensignatur zeigt unter **Vorschau der Methodensignatur**.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="remarks"></a>Hinweise  
 Bei Verwendung der **Methode extrahieren** Befehl, die neue Methode nach der Source-Element in der gleichen Klasse eingefügt wird.  
  
## <a name="partial-types"></a>Partielle Typen  
 Wenn die Klasse ein partieller Typ, klicken Sie dann ist **Methode extrahieren** generiert die neue Methode sofort nach der Quelle-Element. **Methode extrahieren** bestimmt die Signatur der neuen Methode und erstellt eine statische Methode, wenn keine Instanzdaten vom Code in die neue Methode verwiesen werden.  
  
## <a name="generic-type-parameters"></a>Generische Typparameter  
 Wenn Sie eine Methode, die einen nicht eingeschränkte generischer Typparameter hat extrahieren, wird der generierte Code nicht hinzufügen der `ref` Modifizierer an diesen Parameter, wenn ein Wert zugewiesen wird. Wenn die extrahierte Methode Verweistypen als das generische Typargument unterstützt, sollten Sie manuell hinzufügen der `ref` Modifizierer, um den Parameter in der Methodensignatur.  
  
## <a name="anonymous-methods"></a>Anonyme Methoden  
 Wenn Sie versuchen, die Teil einer anonymen Methode extrahieren, die einen Verweis auf eine lokale Variable, die enthält entweder deklariert oder außerhalb der anonymen Methode verwiesen wird, klicken Sie dann warnt Visual Studio Sie, zu möglichen semantischen Änderungen.  
  
 Wenn den Wert einer lokalen Variablen in eine anonyme Methode verwendet wird, wird der Wert im Moment abgerufen, wenn die anonyme Methode ausgeführt wird. Wenn eine anonyme Methode in einer anderen Methode extrahiert wurde, wird der Wert der lokalen Variablen zum Zeitpunkt des Aufrufs der extrahierten Methode abgerufen.  
  
 Das folgende Beispiel veranschaulicht diese semantische Änderung. Wenn dieser Code, klicken Sie dann ausgeführt wird **11** werden auf der Konsole ausgegeben. Bei Verwendung von **Methode extrahieren** zum Extrahieren von des Codebereich an, die durch die Codekommentare, die in eine eigene Methode markiert ist, und führen Sie dann die umgestalteten Code dann **10** werden auf der Konsole ausgegeben.  
  
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
  
 Stellen Sie um diese Situation zu vermeiden die lokalen Variablen, die in den Feldern der anonymen Methode der Klasse verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Refactoring (C#)](refactoring-csharp.md)
---
title: "Umgestaltung &quot;Methode extrahieren&quot; (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.extractmethod"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Umgestaltung [C#], Methode extrahieren"
  - "Methode extrahieren (Umgestaltungsvorgang) [C#]"
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Umgestaltung &quot;Methode extrahieren&quot; (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Methode extrahieren** ist ein Umgestaltungsvorgang und bietet eine einfache Möglichkeit, eine neue Methode auf der Grundlage eines Codefragments in einem vorhandenen Member zu erstellen.  
  
 Mithilfe von **Methode extrahieren** können Sie eine neue Methode erstellen, indem Sie eine Codeauswahl aus dem Codeblock eines vorhandenen Members heraus extrahieren.  Die neue, extrahierte Methode enthält den ausgewählten Code, und der im vorhandenen Member ausgewählte Code wird durch einen Aufruf der neuen Methode ersetzt.  Durch die Umwandlung eines Codefragments in eine eigene Methode haben Sie die Möglichkeit, Code schnell und exakt neu zu ordnen. Dadurch verbessern Sie die Wiederverwendbarkeit und die Lesbarkeit.  
  
 **Methode extrahieren** bietet folgende Vorteile:  
  
-   Optimale Codierungstechniken aufgrund diskreter, wiederverwendbarer Methoden.  
  
-   Selbstdokumentierender Code durch gute Organisation.  
  
     Bei Verwendung beschreibender Namen können hoch entwickelte Methoden mehr Informationen einlesen als eine Reihe von Kommentaren.  
  
-   Erstellung von Methoden mit höherer Granularität, um Überschreibungen zu vereinfachen.  
  
-   Vorkommen von doppeltem Code werden reduziert.  
  
### So verwenden Sie "Methode extrahieren"  
  
1.  Erstellen Sie eine Konsolenanwendung mit dem Namen `ExtractMethod`, und ersetzen Sie `Program` durch den folgenden Beispielcode.  
  
    ```c#  
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
  
2.  Wählen Sie das Codefragment aus, das Sie extrahieren möchten:  
  
    ```c#  
    double area = PI * radius * radius;  
  
    ```  
  
3.  Klicken Sie im Menü **Umgestalten** auf **Methode extrahieren**.  
  
     Das Dialogfeld **Methode extrahieren** wird angezeigt.  
  
     Alternativ können Sie auch die Tastenkombination STRG\+R, M drücken, um das Dialogfeld **Methode extrahieren** anzuzeigen.  
  
     Sie können auch mit der rechten Maustaste auf den ausgewählten Code klicken, auf **Umgestalten** zeigen und dann auf **Methode extrahieren** klicken, um das Dialogfeld **Methode extrahieren** aufzurufen.  
  
4.  Geben Sie im Feld **Neuer Methodenname** einen Namen für die neue Methode ein, z. B. `CircleArea`.  
  
     Eine Vorschau der neuen Methodensignatur wird unter **Vorschau der Methodensignatur** angezeigt.  
  
5.  Klicken Sie auf **OK**.  
  
## Hinweise  
 Bei Verwendung des Befehls **Methode extrahieren** wird die neue Methode nach dem Quellmember in derselben Klasse eingefügt.  
  
## Partielle Typen  
 Wenn die Klasse ein partieller Typ ist, erzeugt **Methode extrahieren** eine neue Methode, die unmittelbar auf den Quellmember folgt.  **Methode extrahieren** bestimmt die Signatur der neuen Methode und erstellt eine statische Methode, wenn von dem Code in der neuen Methode nicht auf Instanzdaten verwiesen wird.  
  
## Parameter für generische Typen  
 Wenn Sie eine Methode extrahieren, die über einen Parameter mit einem nicht beschränkten generischen Typ verfügt, fügt der generierte Code dem Parameter nur dann einen `ref`\-Modifizierer hinzu, wenn dem Parameter ein Wert zugewiesen wurde.  Wenn die extrahierte Methode Referenztypen als Argument für den generischen Typ unterstützt, sollten Sie dem Parameter in der Methodensignatur den `ref`\-Modifizierer manuell hinzufügen.  
  
## Anonyme Methoden  
 Wenn Sie versuchen, ein Fragment aus einer anonymen Methode zu extrahieren, das einen Verweis auf eine außerhalb der anonymen Methode deklarierte oder referenzierte lokale Variable enthält, zeigt Visual Studio eine Warnung zu möglichen semantischen Änderungen an.  
  
 Wenn eine anonyme Methode den Wert einer lokalen Variablen verwendet, wird der Wert zu dem Zeitpunkt abgerufen, zu dem die anonyme Methode ausgeführt wird.  Wenn eine anonyme Methode in eine andere Methode extrahiert wird, wird der Wert der lokalen Variablen abgerufen, wenn die extrahierte Methode aufgerufen wird.  
  
 Diese semantische Änderung wird anhand des folgenden Beispiels veranschaulicht.  Wenn dieser Code ausgeführt wird, wird **11** auf der Konsole ausgegeben.  Wenn Sie einen durch Codekommentare gekennzeichneten Bereich mit **Methode extrahieren** in eine eigene Methode extrahieren und dann den umgestalteten Code ausführen, wird **10** auf der Konsole ausgegeben.  
  
```c#  
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
  
 Um diese Situation zu vermeiden, konfigurieren Sie die in der anonymen Methode verwendeten lokalen Variablen als Felder der Klasse.  
  
## Siehe auch  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)
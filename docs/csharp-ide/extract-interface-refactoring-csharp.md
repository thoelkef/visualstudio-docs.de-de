---
title: "Extract Interface Refactoring (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.extractinterface"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Extract Interface"
  - "Extract Interface refactoring operation [C#]"
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Extract Interface Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Schnittstelle extrahieren ist ein Umgestaltungsvorgang, der eine einfache Möglichkeit zum Erstellen einer neuen Schnittstelle mit Membern aus einer vorhandenen Klasse, Struktur oder Schnittstelle bietet.  
  
 Wenn mehrere Clients dasselbe Subset von Membern aus einer Klasse, Struktur oder Schnittstelle verwenden oder wenn mehrere Klassen, Strukturen oder Schnittstellen ein gemeinsames Subset von Membern haben, kann es hilfreich sein, das Membersubset in eine Schnittstelle aufzunehmen.  Weitere Informationen zur Verwendung von Schnittstellen finden Sie unter [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Durch Schnittstelle extrahieren wird eine Schnittstelle in einer neuen Datei generiert und der Cursor an den Anfang der neuen Datei gesetzt.  Im Dialogfeld **Schnittstelle extrahieren** können Sie angeben, welche Member in die neue Schnittstelle zu extrahieren sind sowie den Namen der neuen Schnittstelle und den Namen der generierten Datei angeben.  
  
### So verwenden Sie "Schnittstelle extrahieren"  
  
1.  Erstellen Sie eine Konsolenanwendung mit dem Namen `ExtractInterface`, und ersetzen Sie `Program` durch den folgenden Code.  
  
    ```c#  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Wählen Sie, während sich der Cursor in `MethodB` befindet, im Menü **Umgestalten** den Befehl **Schnittstelle extrahieren** aus.  
  
     Das Dialogfeld **Schnittstelle extrahieren** wird angezeigt.  
  
     Sie können auch die Tastenkombination STRG\+R, I drücken, um das Dialogfeld **Schnittstelle extrahieren** anzuzeigen.  
  
     Sie können auch mit der rechten Maustaste klicken, auf **Umgestalten** zeigen und dann auf **Schnittstelle extrahieren** klicken, um das Dialogfeld **Schnittstelle extrahieren** anzuzeigen.  
  
3.  Klicken Sie auf **Alle auswählen**.  
  
4.  Klicken Sie auf **OK**.  
  
     Die neue Datei IProtoA.cs und folgender Code werden angezeigt:  
  
    ```c#  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## Hinweise  
 Dieses Feature ist nur verfügbar, wenn sich der Cursor in der Klasse, Struktur oder Schnittstelle befindet, die die zu extrahierenden Member enthält.  Wenn sich der Cursor an dieser Position befindet, rufen Sie den Umgestaltungsvorgang Schnittstelle extrahieren auf.  
  
 Wenn Sie Schnittstelle extrahieren für eine Klasse oder Struktur aufrufen, wird die Liste der Basen und Schnittstellen geändert, um den neuen Schnittstellennamen aufzunehmen.  Wenn Sie Schnittstelle extrahieren für eine Schnittstelle aufrufen, wird die Liste der Basen und Schnittstellen nicht geändert.  
  
## Siehe auch  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)
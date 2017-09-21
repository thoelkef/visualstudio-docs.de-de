---
title: "Umgestaltung &quot;Parameter entfernen&quot; (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.remove"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Parameter [C#], Entfernen"
  - "Umgestaltung [C#], Parameter entfernen"
  - "Umgestaltung "Parameter entfernen" [C#]"
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Umgestaltung &quot;Parameter entfernen&quot; (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Remove Parameters` ist ein Umgestaltungsvorgang, mit dem Sie Parameter von Methoden, Indexern und Delegaten entfernen können.  Durch Metadaten entfernen wird die Deklaration geändert, und an allen Positionen, an denen der Member aufgerufen wird, wird der Parameter entsprechend der neuen Deklaration entfernt.  
  
 Sie führen den Vorgang zum Entfernen von Parametern aus, indem Sie zunächst den Cursor auf einer Methode, einem Indexer oder Delegaten positionieren.  Sobald sich der Cursor an der richtigen Position befindet, können Sie den Vorgang `Parameters` entfernen aufrufen, indem Sie auf das Menü **Umgestalten** klicken, die Tastenkombination drücken oder den Befehl aus dem Kontextmenü auswählen.  
  
> [!NOTE]
>  Der erste Parameter in einer Erweiterungsmethode kann nicht entfernt werden.  
  
### So entfernen Sie Parameter  
  
1.  Erstellen Sie eine Konsolenanwendung mit dem Namen `RemoveParameters`, und ersetzen Sie `Program` durch den folgenden Code.  
  
    ```c#  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  Positionieren Sie den Cursor entweder in der Methodendeklaration oder im Methodenaufruf der Methode `A`.  
  
3.  Wählen Sie im Menü **Umgestalten** den Eintrag **Parameter entfernen**, um das Dialogfeld **Parameter entfernen** anzuzeigen.  
  
     Sie können auch die Tastenkombination STRG\+R, STRG\+V drücken, um das Dialogfeld **Parameter entfernen** anzuzeigen.  
  
     Sie können auch mit der rechten Maustaste klicken, im Kontextmenü auf **Umgestalten** zeigen und dann auf **Parameter entfernen** klicken, um das Dialogfeld **Parameter entfernen** anzuzeigen.  
  
4.  Positionieren Sie den Cursor mithilfe des Felds **Parameter** auf `int i`, und klicken Sie dann auf **Entfernen**.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Klicken Sie im Dialogfeld **Vorschau der Änderungen \- Parameter entfernen** auf **Übernehmen**.  
  
## Hinweise  
 Sie können Parameter aus einer Methodendeklaration oder einem Methodenaufruf entfernen.  Positionieren Sie den Cursor in der Methodendeklaration oder im Delegatennamen, und rufen Sie Parameter entfernen auf.  
  
> [!CAUTION]
>  Mithilfe von Parameter entfernen können Sie einen Parameter entfernen, auf den im Text des Members verwiesen wird. Die Verweise auf diesen Parameter im Methodentext werden jedoch nicht entfernt.  Dies kann zu Buildfehlern im Code führen.  Sie können jedoch das Dialogfeld **Vorschau der Änderungen** verwenden, um den Code zu überprüfen, bevor Sie den Umgestaltungsvorgang ausführen.  
  
 Wenn ein zu entfernender Parameter während eines Methodenaufrufs geändert wird, wird mit dem Parameter selbst auch die Änderung entfernt.  Wenn ein Methodenaufruf durch den Umgestaltungsvorgang beispielsweise von  
  
```c#  
MyMethod(param1++, param2);  
```  
  
 zu  
  
```c#  
MyMethod(param2);  
```  
  
 geändert wird, wird `param1` nicht erhöht.  
  
## Siehe auch  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)
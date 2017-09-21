---
title: "Reorder Parameters Refactoring (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.reorder"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Reorder Parameters"
  - "Reorder Parameters refactoring [C#]"
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Reorder Parameters Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Reorder Parameters` ist ein Visual C\#\-Umgestaltungsvorgang, mit dem Sie die Reihenfolge der Parameter für Methoden, Indexer und Delegaten leicht ändern können.  Durch `Reorder Parameters` wird die Deklaration geändert, und an allen Positionen, an denen der Member aufgerufen wird, werden die Parameter entsprechend der neuen Reihenfolge neu angeordnet.  
  
 Sie können den Vorgang `Reorder Parameters` ausführen, indem Sie den Cursor auf einer Methode, einem Indexer oder einem Delegaten positionieren.  Nachdem der Cursor richtig positioniert wurde, rufen Sie den `Reorder Parameters`\-Vorgang auf, indem Sie die Tastenkombination drücken oder indem Sie im Kontextmenü auf den Befehl klicken.  
  
> [!NOTE]
>  Der erste Parameter in einer Erweiterungsmethode kann nicht neu angeordnet werden.  
  
### So ordnen Sie Parameter neu an  
  
1.  Erstellen Sie eine Klassenbibliothek mit dem Namen `ReorderParameters`, und ersetzen Sie dann `Class1` durch folgendes Codebeispiel.  
  
    ```c#  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Positionieren Sie den Cursor entweder in der Methodendeklaration oder im Methodenaufruf auf `MethodB`.  
  
3.  Klicken Sie im Menü **Umgestalten** auf **Parameter neu anordnen**.  
  
     Das Dialogfeld **Parameter neu anordnen** wird angezeigt.  
  
4.  Wählen Sie im Dialogfeld **Parameter neu anordnen** in der Liste **Parameter** `int i`, und klicken Sie dann auf die Schaltfläche Nach unten.  
  
     Alternativ können Sie `int i` in der Liste **Parameter** an eine Position nach `bool b` ziehen.  
  
5.  Klicken Sie im Dialogfeld **Parameter neu anordnen** auf **OK**.  
  
     Wenn im Dialogfeld **Parameter neu anordnen** die Option **Vorschau der Verweisänderungen** aktiviert ist, wird das Dialogfeld **Vorschau der Änderungen \- Parameter neu anordnen** eingeblendet.  Das Dialogfeld enthält eine Vorschau der Änderungen, die in der Parameterliste für `MethodB` sowohl in der Signatur als auch im Methodenaufruf vorgenommen wurden.  
  
    1.  Falls das Dialogfeld **Vorschau der Änderungen \- Parameter neu anordnen** angezeigt wird, klicken Sie auf **Übernehmen**.  
  
         In diesem Beispiel werden die Methodendeklaration und sämtliche Aufrufsites der Methode für `MethodB` aktualisiert.  
  
## Hinweise  
 Sie können Parameter aus einer Methodendeklaration oder einem Methodenaufruf neu anordnen.  Positionieren Sie den Cursor in der Methoden\- oder Delegatdeklaration, nicht jedoch im Text.  
  
## Siehe auch  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)
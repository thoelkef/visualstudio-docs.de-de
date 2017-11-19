---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: Neuanordnen von Parametern, die Umgestaltung (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.reorder
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3469e9ae7101c9e180fba5558fce389c6dfcc72d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="reorder-parameters-refactoring-c"></a>Refactoring „Parameter neu anordnen“ (C#)
`Reorder Parameters`ist eine Visual C#-Umgestaltungsvorgang, die eine einfache Möglichkeit zum Ändern der Reihenfolge der Parameter für Methoden, Indexer und Delegaten bereitstellt. `Reorder Parameters`Ändert die Deklaration und überall, wo das Element wird aufgerufen, werden die Parameter entsprechend die neue Reihenfolge neu angeordnet.  
  
 Zum Ausführen der `Reorder Parameters` Vorgang, platzieren Sie den Cursor auf oder neben einer Methode, Indexer oder einem Delegaten. Wenn Sie der Cursor in Position befindet, rufen Sie die `Reorder Parameters` Vorgang durch Drücken der Tastenkombination zugreifen, oder indem Sie den Befehl aus dem Kontextmenü.  
  
> [!NOTE]
>  Sie können den ersten Parameter in einer Erweiterungsmethode nicht ändern.  
  
### <a name="to-reorder-parameters"></a>Parameter neu anordnen.  
  
1.  Erstellen Sie eine Klassenbibliothek mit dem Namen `ReorderParameters`, und Ersetzen Sie `Class1` mit dem folgenden Beispielcode.  
  
    ```csharp  
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
  
2.  Platzieren Sie den Cursor auf `MethodB`, entweder in der Deklaration der Methode oder dem Aufruf der Methode.  
  
3.  Auf der **Umgestalten** Menü klicken Sie auf **Parameter neu anordnen**.  
  
     Die **Parameter neu anordnen** Dialogfeld wird angezeigt.  
  
4.  In der **Parameter neu anordnen** wählen Sie im Dialogfeld `int i` in der **Parameter** aus, und klicken Sie dann auf die Schaltfläche nach unten.  
  
     Alternativ können Sie ziehen `int i` nach `bool b` in der **Parameter** Liste.  
  
5.  In der **Parameter neu anordnen** (Dialogfeld), klicken Sie auf **OK**.  
  
     Wenn die **Vorschau der Änderungen Verweis** ausgewählt ist die **Parameter neu anordnen** (Dialogfeld), die **Vorschau der Änderungen - Parameter neu anordnen** Dialogfeld wird angezeigt. Es bietet eine Vorschau der Änderungen in der Parameterliste für `MethodB` in der Signatur und dem Aufruf der Methode.  
  
    1.  Wenn die **Vorschau der Änderungen - Parameter neu anordnen** Dialogfeld angezeigt wird, klicken Sie auf **übernehmen**.  
  
         In diesem Beispiel wird die Deklaration der Methode und alle der Methodenaufruf Websites für `MethodB` aktualisiert werden.  
  
## <a name="remarks"></a>Hinweise  
 Sie können die Parameter aus einer Methodendeklaration oder einem Methodenaufruf neu anordnen. Positionieren Sie den Cursor auf oder neben der Deklaration Methode oder der Delegat aber nicht im Text.  
  
## <a name="see-also"></a>Siehe auch  
 [Refactoring (C#)](refactoring-csharp.md)
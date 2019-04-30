---
title: Neuanordnen von Parametern (C#) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: daf77a60256e59cabd176990f3642a2206a7f0d8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444546"
---
# <a name="reorder-parameters-refactoring-c"></a>Umgestaltung "Parameter neu anordnen" (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` ist ein Visual C#-Vorgang refactoring, die eine einfache Möglichkeit zum Ändern der Reihenfolge der Parameter für Methoden, Indexer und Delegaten bereitstellt. `Reorder Parameters` Ändert die Deklaration, und an allen Positionen, in dem das Element aufgerufen wird, werden die Parameter entsprechend die neue Reihenfolge neu angeordnet.  
  
 Zum Ausführen der `Reorder Parameters` -Operation, platzieren Sie den Cursor auf oder neben einer Methode, Indexer oder Delegat. Wenn der Cursor positioniert wurde, rufen die `Reorder Parameters` Vorgang durch Drücken der Tastenkombination oder durch Klicken auf den Befehl aus dem Kontextmenü.  
  
> [!NOTE]
> Sie können den ersten Parameter in eine Erweiterungsmethode nicht ändern.  
  
### <a name="to-reorder-parameters"></a>Parameter neu anordnen.  
  
1. Erstellen einer Klassenbibliothek mit dem Namen `ReorderParameters`, und Ersetzen Sie `Class1` mit dem folgenden Beispielcode.  
  
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
  
2. Platzieren Sie den Cursor auf `MethodB`, entweder in der Deklaration der Methode oder der Aufruf der Methode.  
  
3. Auf der **Umgestalten** Menü klicken Sie auf **Parameter neu anordnen**.  
  
     Die **Parameter neu anordnen** Dialogfeld wird angezeigt.  
  
4. In der **Parameter neu anordnen** wählen Sie im Dialogfeld `int i` in die **Parameter** aus, und klicken Sie dann auf die Schaltfläche nach unten.  
  
     Alternativ können Sie ziehen `int i` nach `bool b` in die **Parameter** Liste.  
  
5. In der **Parameter neu anordnen** Dialogfeld klicken Sie auf **OK**.  
  
     Wenn die **Vorschau der verweisänderungen** Option ausgewählt ist, der **Parameter neu anordnen** im Dialogfeld die **Vorschau der Änderungen – Parameter neu anordnen** Dialogfeld wird angezeigt. Es bietet eine Vorschau der Änderungen in der Parameterliste für `MethodB` in der Signatur und den Methodenaufruf.  
  
    1. Wenn die **Vorschau der Änderungen – Parameter neu anordnen** klicken Sie im angezeigten Dialogfeld **übernehmen**.  
  
         In diesem Beispiel ist die Deklaration der Methode und alle der Methodenaufruf Websites für `MethodB` werden aktualisiert.  
  
## <a name="remarks"></a>Hinweise  
 Sie können die Parameter aus der Deklaration einer Methode oder ein Methodenaufruf neu anordnen. Positionieren Sie den Cursor auf oder neben der Deklaration der Methoden- oder Delegatparameter, aber nicht im Text.  
  
## <a name="see-also"></a>Siehe auch  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)
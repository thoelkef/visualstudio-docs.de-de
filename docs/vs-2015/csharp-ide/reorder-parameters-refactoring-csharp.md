---
title: Refactoring für Parameter neu anordnen (C#) | Microsoft-Dokumentation
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e39564fb108b63859620e2c4a650608cdf1e7e82
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673145"
---
# <a name="reorder-parameters-refactoring-c"></a>Umgestaltung "Parameter neu anordnen" (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` ist ein visueller C# Refactoring-Vorgang, der eine einfache Möglichkeit bietet, die Reihenfolge der Parameter für Methoden, Indexer und Delegaten zu ändern. `Reorder Parameters` die Deklaration ändert, und an allen Stellen, an denen der Member aufgerufen wird, werden die Parameter neu angeordnet, um die neue Reihenfolge widerzuspiegeln.

 Um den `Reorder Parameters` Vorgang auszuführen, platzieren Sie den Cursor am oder neben einer Methode, einem Indexer oder einem Delegaten. Wenn sich der Cursor in der Position befindet, rufen Sie den `Reorder Parameters` Vorgang durch Drücken der Tastenkombination oder durch Klicken auf den Befehl im Kontextmenü auf.

> [!NOTE]
> Sie können den ersten Parameter in einer Erweiterungsmethode nicht neu anordnen.

### <a name="to-reorder-parameters"></a>So ordnen Sie Parameter neu an

1. Erstellen Sie eine Klassenbibliothek mit dem Namen `ReorderParameters`, und ersetzen Sie `Class1` durch den folgenden Beispielcode.

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

2. Platzieren Sie den Cursor in `MethodB`, entweder in der Methoden Deklaration oder im Methoden Aufruf.

3. Klicken Sie im Menü **umgestalten** auf **Parameter neu anordnen**.

     Das Dialogfeld **Parameter neu anordnen** wird angezeigt.

4. Wählen Sie im Dialogfeld **Parameter neu anordnen** in der Liste **Parameter** `int i` aus, und klicken Sie dann auf die Schaltfläche nach unten.

     Alternativ können Sie `int i` nach `bool b` in der **Parameter** Liste ziehen.

5. Klicken Sie im Dialogfeld **Parameter neu anordnen** auf **OK**.

     Wenn die Option **Vorschau der Verweis Änderungen** im Dialogfeld **Parameter neu anordnen** ausgewählt ist, wird das Dialogfeld **Vorschau der Änderungen-Parameter neu anordnen** angezeigt. Sie stellt eine Vorschau der Änderungen in der Parameterliste für `MethodB` sowohl im Signatur-als auch im Methoden aufrufswert bereit.

    1. Wenn das Dialogfeld **Vorschau der Änderungen-Parameter neu anordnen** angezeigt wird **, klicken Sie**auf übernehmen.

         In diesem Beispiel werden die Methoden Deklaration und alle Methoden Aufrufsites für `MethodB` aktualisiert.

## <a name="remarks"></a>Hinweise
 Sie können Parameter aus einer Methoden Deklaration oder einem Methoden aufrufneu anordnen. Positionieren Sie den Cursor am oder neben der Methode oder Delegatdeklaration, aber nicht im Text.

## <a name="see-also"></a>Siehe auch
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)
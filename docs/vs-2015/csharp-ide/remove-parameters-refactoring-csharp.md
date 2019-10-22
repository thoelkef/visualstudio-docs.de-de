---
title: Refactoring "Parameter entfernenC#" () | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40c373c3575f007952143e29c8dfc2cfac3d080f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667496"
---
# <a name="remove-parameters-refactoring-c"></a>Umgestaltung "Parameter entfernen" (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` ist ein Refactoring-Vorgang, der eine einfache Möglichkeit bietet, Parameter aus Methoden, indexatoren oder Delegaten zu entfernen. Parameter entfernen ändert die Deklaration. an allen Speicherorten, an denen der Member aufgerufen wird, wird der Parameter entfernt, um die neue Deklaration widerzuspiegeln.

 Sie führen den Remove Parameters-Vorgang aus, indem Sie den Cursor zuerst auf einer Methode, einem Indexer oder einem Delegaten positionieren. Wenn sich der Cursor in der Position befindet, klicken Sie zum Aufrufen des Vorgangs zum Entfernen von `Parameters` auf das Menü **umgestalten** , drücken Sie die Tastenkombination, oder wählen Sie den Befehl im Kontextmenü aus.

> [!NOTE]
> Der erste Parameter kann nicht in einer Erweiterungsmethode entfernt werden.

### <a name="to-remove-parameters"></a>So entfernen Sie Parameter

1. Erstellen Sie eine Konsolenanwendung mit dem Namen `RemoveParameters`, und ersetzen Sie `Program` durch den folgenden Code.

    ```csharp
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

2. Platzieren Sie den Cursor in der Methode `A`, entweder in der Methoden Deklaration oder im Methoden Aufruf.

3. Wählen Sie im Menü **umgestalten** die Option **Parameter entfernen** aus, um das Dialogfeld **Parameter entfernen** anzuzeigen.

     Sie können auch die Tastenkombination STRG + R, V eingeben, um das Dialogfeld **Parameter entfernen** anzuzeigen.

     Sie können auch mit der rechten Maustaste auf den Cursor klicken, auf **umgestalten**zeigen und dann auf **Parameter entfernen** klicken, um das Dialogfeld **Parameter entfernen** anzuzeigen.

4. Positionieren Sie den Cursor mithilfe des **Parameters** -Felds auf `int i`, und klicken Sie dann auf **Entfernen**.

5. Klicken Sie auf **OK**.

6. Klicken Sie im Dialogfeld **Vorschau der Änderungen – Parameter entfernen** auf **anwenden**.

## <a name="remarks"></a>Hinweise
 Sie können Parameter aus einer Methoden Deklaration oder einem Methoden aufrufaus entfernen. Positionieren Sie den Cursor in der Methoden Deklaration oder im Delegatnamen, und rufen Sie Parameter entfernen auf.

> [!CAUTION]
> Remove Parameters ermöglicht Ihnen das Entfernen eines Parameters, auf den im Hauptteil des Members verwiesen wird, aber es werden nicht die Verweise auf diesen Parameter im Methoden Text entfernt. Dadurch können Buildfehler in Ihren Code eingeführt werden. Sie können jedoch das Dialogfeld **Vorschau der Änderungen** verwenden, um den Code zu überprüfen, bevor Sie den Refactoring-Vorgang ausführen.

 Wenn ein zu entfernender Parameter während des Aufrufes einer Methode geändert wird, wird durch das Entfernen des Parameters ebenfalls die Änderung entfernt. Wenn z. b. ein Methoden Aufrufwert von

```csharp
MyMethod(param1++, param2);
```

 auf

```csharp
MyMethod(param2);
```

 beim Umgestaltungs Vorgang werden `param1` nicht inkrementiert.

## <a name="see-also"></a>Siehe auch
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)
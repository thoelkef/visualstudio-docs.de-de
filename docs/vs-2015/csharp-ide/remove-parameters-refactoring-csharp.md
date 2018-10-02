---
title: Entfernen von Parametern (C#) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 529950d72ac11ebfd443a85db597adfcbc89bba1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521792"
---
# <a name="remove-parameters-refactoring-c"></a>Umgestaltung "Parameter entfernen" (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` ist ein refactoring Vorgang, der eine einfache Möglichkeit, Parameter aus Methoden, Indexern oder Delegaten entfernen bereitstellt. Entfernen Sie die Deklaration Parameter geändert; der Parameter wird an allen Positionen, in dem der Member aufgerufen wird, entsprechend die neue Deklaration entfernt.  
  
 Führen Sie den Parameter entfernen-Vorgang durch erste Positionieren des Cursors auf eine Methode, Indexer oder Delegat. Während der Cursor an der Position, zum Aufrufen des Remove `Parameters` -Vorgang, klicken Sie auf die **Umgestalten** Menü, drücken Sie die Tastenkombination, oder wählen Sie im Kontextmenü den Befehl.  
  
> [!NOTE]
>  Sie können nicht den ersten Parameter einer Erweiterungsmethode entfernen.  
  
### <a name="to-remove-parameters"></a>Um Parameter zu entfernen.  
  
1.  Erstellen Sie eine Konsolenanwendung namens `RemoveParameters`, und Ersetzen Sie `Program` durch den folgenden Code.  
  
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
  
2.  Platzieren Sie den Cursor auf die Methode `A`, entweder in der Deklaration der Methode oder der Aufruf der Methode.  
  
3.  Von der **Umgestalten** , wählen Sie im Menü **Parameter entfernen** zum Anzeigen der **Parameter entfernen** Dialogfeld.  
  
     Sie können auch die Tastenkombination STRG + R, V anzuzeigende eingeben der **Parameter entfernen** Dialogfeld.  
  
     Sie können auch mit der rechten Maustaste des Cursors, zeigen Sie auf **Umgestalten**, und klicken Sie dann auf **Parameter entfernen** zum Anzeigen der **Parameter entfernen** Dialogfeld.  
  
4.  Mithilfe der **Parameter** Feld, positionieren Sie den Cursor auf `int i`, und klicken Sie dann auf **entfernen**.  
  
5.  Klicken Sie auf **OK**.  
  
6.  In der **Vorschau der Änderungen – Parameter entfernen** Dialogfeld klicken Sie auf **übernehmen**.  
  
## <a name="remarks"></a>Hinweise  
 Sie können die Parameter aus der Deklaration einer Methode oder ein Methodenaufruf entfernen. Positionieren Sie des Cursors in der Deklaration oder Delegaten Name der Methode aus, und rufen Sie die Parameter zu entfernen.  
  
> [!CAUTION]
>  Entfernen Sie die Parameter ermöglicht, die Sie entfernen einen Parameter, der auf die verwiesen wird im Text der das Element, sondern die Verweise auf diesen Parameter nicht im Methodentext entfernt werden. Dies kann in Ihren Code zu Buildfehlern führen. Sie können jedoch die **Vorschau der Änderungen** Dialogfeld Überprüfung des Codes vor dem Ausführen des Umgestaltungsvorgangs.  
  
 Wenn ein Parameter, die entfernt werden, während des Aufrufs einer Methode geändert wird, wird das Entfernen des Parameters auch die Änderung entfernt. Z. B. wenn ein Methodenaufruf werden von geändert  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 auf  
  
```csharp  
MyMethod(param2);  
```  
  
 durch den Umgestaltungsvorgang `param1` wird nicht erhöht.  
  
## <a name="see-also"></a>Siehe auch  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)
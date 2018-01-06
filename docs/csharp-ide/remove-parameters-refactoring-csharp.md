---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: Entfernen Sie die Parameter, die Umgestaltung (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.remove
dev_langs: CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 549914476db028cc5135de3c954ac841ab2da628
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="remove-parameters-refactoring-c"></a>Umgestaltung "Parameter entfernen" (C#)
`Remove Parameters`ist ein Umgestaltungsvorgang, der eine einfache Möglichkeit zum Entfernen von Parametern von Methoden, Indexer oder Delegaten bereitstellt. Entfernen Sie die Deklaration Parameter Änderungen; überall, wo das Element aufgerufen wird, wird der Parameter entsprechend die neue Deklaration entfernt.  
  
 Den Parameter entfernen-Vorgang wird ausgeführt, indem Sie zunächst den Cursor auf eine Methode, Indexer oder Delegaten positionieren. Während der Cursor in Position, aufzurufenden entfernen `Parameters` Vorgang, klicken Sie auf die **Umgestalten** Menü, drücken Sie die Tastenkombination, oder wählen Sie im Kontextmenü den Befehl.  
  
> [!NOTE]
>  Den ersten Parameter kann nicht in einer Erweiterungsmethode entfernt werden.  
  
### <a name="to-remove-parameters"></a>So entfernen Sie die Parameter  
  
1.  Erstellen Sie eine Konsolenanwendung, die mit dem Namen `RemoveParameters`, und Ersetzen Sie `Program` durch den folgenden Code.  
  
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
  
2.  Platzieren Sie den Cursor auf die Methode `A`, entweder in der Deklaration der Methode oder dem Aufruf der Methode.  
  
3.  Aus der **Umgestalten** klicken Sie im Menü **Parameter entfernen** zum Anzeigen der **Parameter entfernen** (Dialogfeld).  
  
     Sie können auch die Tastenkombination STRG + R, V anzuzeigenden eingeben der **Parameter entfernen** (Dialogfeld).  
  
     Sie können auch mit der rechten Maustaste des Mauszeiger, zeigen Sie auf **Umgestalten**, und klicken Sie dann auf **Parameter entfernen** zum Anzeigen der **Parameter entfernen** (Dialogfeld).  
  
4.  Mithilfe der **Parameter** Feld, positionieren Sie den Cursor auf `int i`, und klicken Sie dann auf **entfernen**.  
  
5.  Klicken Sie auf **OK**.  
  
6.  In der **Vorschau der Änderungen, Parameter entfernen** (Dialogfeld), klicken Sie auf **übernehmen**.  
  
## <a name="remarks"></a>Hinweise  
 Sie können Parameter aus einer Methodendeklaration oder einem Methodenaufruf entfernen. Positionieren Sie den Cursor in den Methodennamen der Deklaration oder Delegaten, und rufen Sie Parameter entfernen.  
  
> [!CAUTION]
>  Entfernen Sie die Parameter ermöglicht das Entfernen ein Parameters, auf die verwiesen wird, wird im Text der Member, aber es die Verweise auf diesen Parameter nicht im Methodentext entfernt. Dies kann Buildfehler in Ihren Code einführen. Sie können jedoch die **Vorschau der Änderungen** Dialogfeld Überprüfung des Codes vor dem Ausführen der Umgestaltungsvorgang.  
  
 Wenn ein Parameter entfernt wird während des Aufrufs einer Methode geändert wird, wird das Entfernen des Parameters auch die Änderung entfernt. Z. B. wenn ein Methodenaufruf werden von geändert  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 auf  
  
```csharp  
MyMethod(param2);  
```  
  
 durch den Umgestaltungsvorgang `param1` wird nicht erhöht werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Refactoring (C#)](refactoring-csharp.md)
---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-interface
title: Umgestaltung (c#) Schnittstelle extrahieren | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e3e606a86f5989ca928e0b093b564f997f92a559
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="extract-interface-refactoring-c"></a>Refactoring „Schnittstelle extrahieren“ (C#)
Schnittstelle extrahieren ist ein Umgestaltungsvorgang, der können eine einfache Möglichkeit, eine neue Schnittstelle mit Elementen zu erstellen, die aus einer vorhandenen Klasse, Struktur oder Schnittstelle stammen.  
  
 Wenn mehrere Clients die gleiche Teilmenge von Elementen aus einer Klasse, Struktur oder Schnittstelle verwenden, oder wenn mehrere Klassen, Strukturen oder Schnittstellen eine Teilmenge von Elementen gemeinsam haben, kann es sinnvoll, stellen die Teilmenge von Elementen in einer Schnittstelle sein. Weitere Informationen zur Verwendung von Schnittstellen finden Sie unter [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Schnittstelle extrahieren eine Schnittstelle in einer neuen Datei generiert, und platziert den Cursor am Anfang der neuen Datei. Sie können angeben, welche Member in die neue Schnittstelle, die Namen der neuen Schnittstelle und den Namen der generierten Datei extrahieren der **Schnittstelle extrahieren** (Dialogfeld).  
  
### <a name="to-use-extract-interface"></a>Schnittstelle extrahieren verwenden  
  
1.  Erstellen Sie eine Konsolenanwendung, die mit dem Namen `ExtractInterface`, und Ersetzen Sie `Program` durch den folgenden Code  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Mit dem Cursor im `MethodB`, und klicken Sie auf **Schnittstelle extrahieren** auf die **Umgestalten** Menü.  
  
     Die **Schnittstelle extrahieren** Dialogfeld wird angezeigt.  
  
     Sie können auch die Tastenkombination STRG + R, ich anzuzeigenden eingeben der **Schnittstelle extrahieren** (Dialogfeld).  
  
     Sie können auch der rechten Maustaste, zeigen Sie auf **Umgestalten**, und klicken Sie dann auf **Schnittstelle extrahieren** zum Anzeigen der **Schnittstelle extrahieren** (Dialogfeld).  
  
3.  Klicken Sie auf **wählen Sie alle**.  
  
4.  Klicken Sie auf **OK**.  
  
     Sie finden die neue Datei, IProtoA.cs und den folgenden Code:  
  
    ```csharp  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion ist nur verfügbar, wenn der Cursor positioniert ist, in der Klasse, Struktur oder Schnittstelle, die die Elemente enthält, die Sie extrahieren möchten. Wenn der Cursor an dieser Position befindet, rufen Sie die Schnittstelle extrahieren (refactoringvorgang).  
  
 Wenn Sie die Schnittstelle extrahieren für eine Klasse oder Struktur aufrufen, wird die Liste der Wissensdatenbanken und Schnittstellen geändert, damit der neue Schnittstellenname enthalten. Wenn Sie die Schnittstelle extrahieren einer Schnittstelle aufrufen, wird die Liste der Wissensdatenbanken und Schnittstellen nicht geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Refactoring (C#)](refactoring-csharp.md)
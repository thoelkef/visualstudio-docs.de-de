---
title: Extrahieren Sie die Schnittstelle Refactoring (c#) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: deb2e446ff051b52e9c34d28abfa99436c064ad6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680905"
---
# <a name="extract-interface-refactoring-c"></a>Refactoring „Schnittstelle extrahieren“ (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Schnittstelle extrahieren wird eine Umgestaltungsvorgang, der können eine einfache Möglichkeit zum Erstellen einer neuen Schnittstelle mit Elementen, die aus einer vorhandenen-Klasse, Struktur oder Schnittstelle stammen.  
  
 Wenn mehrere Clients die gleiche Teilmenge von Elementen aus einer Klasse, Struktur oder Schnittstelle verwenden, oder mehrere Klassen, Strukturen oder Schnittstellen eine Teilmenge von Elementen gemeinsam haben, kann es nützlich, um die Teilmenge von Elementen in einer Schnittstelle enthalten sein. Weitere Informationen zur Verwendung von Schnittstellen finden Sie unter [Schnittstellen](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).  
  
 Schnittstelle extrahieren eine Schnittstelle in einer neuen Datei generiert und platziert den Cursor am Anfang der neuen Datei. Sie können angeben, welche Member in die neue Benutzeroberfläche, den Namen der neuen Schnittstelle und den Namen der generierten Datei extrahieren der **Schnittstelle extrahieren** Dialogfeld.  
  
### <a name="to-use-extract-interface"></a>Mit der Schnittstelle extrahieren  
  
1. Erstellen Sie eine Konsolenanwendung namens `ExtractInterface`, und Ersetzen Sie `Program` durch den folgenden Code  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2. Mit dem Cursor im `MethodB`, und klicken Sie auf **Schnittstelle extrahieren** auf die **Umgestalten** Menü.  
  
     Die **Schnittstelle extrahieren** Dialogfeld wird angezeigt.  
  
     Sie können auch die Tastenkombination STRG + R, ich anzuzeigende eingeben der **Schnittstelle extrahieren** Dialogfeld.  
  
     Sie können auch mit der rechten Maustaste der Maus, zeigen Sie auf **Umgestalten**, und klicken Sie dann auf **Schnittstelle extrahieren** zum Anzeigen der **Schnittstelle extrahieren** Dialogfeld.  
  
3. Klicken Sie auf **wählen Sie alle**.  
  
4. Klicken Sie auf **OK**.  
  
     Daraufhin wird die neue Datei, IProtoA.cs und den folgenden Code:  
  
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
 Diese Funktion ist nur verfügbar, wenn der Cursor positioniert ist, in der Klasse, Struktur oder Schnittstelle, die die Elemente enthält, die Sie extrahieren möchten. Wenn der Cursor in dieser Position befindet, rufen Sie den Umgestaltungsvorgang Schnittstelle extrahieren.  
  
 Wenn Sie die Extract-Schnittstelle für eine Klasse oder Struktur aufrufen, wird die Liste von Basen und Schnittstellen geändert, damit um der Name der neuen Schnittstelle zu enthalten. Wenn Sie die Schnittstelle extrahieren einer Schnittstelle aufrufen, wird die Liste von Basen und Schnittstellen nicht geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)
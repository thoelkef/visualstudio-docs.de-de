---
title: Refactoring der Schnittstelle extrahieren (c#) | Microsoft-Dokumentation
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdcf281e1ace40d1d7cdac0be302810ea173581b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667551"
---
# <a name="extract-interface-refactoring-c"></a>Refactoring „Schnittstelle extrahieren“ (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extract Interface ist ein Refactoring-Vorgang, der eine einfache Möglichkeit bietet, eine neue Schnittstelle mit Membern zu erstellen, die aus einer vorhandenen Klasse, Struktur oder Schnittstelle stammen.

 Wenn mehrere Clients dieselbe Teilmenge von Membern einer Klasse, Struktur oder Schnittstelle verwenden oder wenn mehrere Klassen, Strukturen oder Schnittstellen eine Teilmenge von Elementen gemeinsam haben, kann es hilfreich sein, die Teilmenge von Membern in einer Schnittstelle zu verkörpern. Weitere Informationen zum Verwenden von Schnittstellen finden Sie unter [Schnittstellen](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37).

 Extract Interface generiert eine Schnittstelle in einer neuen Datei und positioniert den Cursor am Anfang der neuen Datei. Mit dem Dialogfeld **Schnittstelle extrahieren** können Sie angeben, welche Member in der neuen Schnittstelle extrahiert werden sollen, den Namen der neuen Schnittstelle und den Namen der generierten Datei.

### <a name="to-use-extract-interface"></a>So verwenden Sie Extract Interface

1. Erstellen Sie eine Konsolenanwendung `ExtractInterface` mit dem Namen, und ersetzen Sie dann `Program` durch den folgenden Code.

    ```csharp
    // Invoke Extract Interface on ProtoA.
    // Note:  the extracted interface will be created in a new file.
    class ProtoA
    {
        public void MethodB(string s) { }
    }
    ```

2. Wenn der Cursor in positioniert `MethodB` ist, und klicken Sie im Menü **umgestalten** auf **Schnittstelle extrahieren** .

     Das Dialogfeld **Schnittstelle extrahieren** wird angezeigt.

     Sie können auch die Tastenkombination STRG + R, I eingeben, um das Dialogfeld **Schnittstelle extrahieren** anzuzeigen.

     Sie können auch mit der rechten Maustaste auf die Maus klicken, auf **umgestalten**zeigen und dann auf **Schnittstelle extrahieren** klicken, um das Dialogfeld **Schnittstelle extrahieren** anzuzeigen.

3. Klicken Sie auf **Alle auswählen**.

4. Klicken Sie auf **OK**.

     Sie sehen die neue Datei IProtoA.cs und den folgenden Code:

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

## <a name="remarks"></a>Bemerkungen
 Diese Funktion ist nur verfügbar, wenn sich der Cursor in der Klasse, Struktur oder Schnittstelle befindet, die die Elemente enthält, die Sie extrahieren möchten. Wenn sich der Cursor an dieser Position befindet, rufen Sie den Refactoring-Vorgang zum Extrahieren der Schnittstelle auf.

 Wenn Sie Extract Interface für eine Klasse oder eine Struktur aufrufen, wird die Liste der Basen und Schnittstellen so geändert, dass Sie den neuen Schnittstellennamen einschließt. Wenn Sie Extract Interface für eine Schnittstelle aufrufen, wird die Liste der Basen und Schnittstellen nicht geändert.

## <a name="see-also"></a>Weitere Informationen
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)
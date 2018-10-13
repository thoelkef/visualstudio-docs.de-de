---
title: Refactoring (c#) Feld kapseln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 35d7e03e30aa5301ee65f15a8591fbccd1de3fcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223543"
---
# <a name="encapsulate-field-refactoring-c"></a>Refactoring „Feld kapseln“ (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die **Feld kapseln** Umgestaltungsvorgang können Sie schnell eine Eigenschaft aus einem vorhandenen Feld erstellen und den Code dann nahtlos mit Verweisen auf die neue Eigenschaft zu aktualisieren.  
  
 Wenn eine [Feld](http://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) ist [öffentliche](http://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), andere Objekte haben Sie direkten Zugriff auf dieses Feld, und können es ändern das Objekt, das dieses Feld besitzt. Mithilfe von [Eigenschaften](http://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) um das Feld kapseln, können Sie den direkten Zugriff auf Felder verhindern.  
  
 Zum Erstellen der neuen Eigenschaft der **Feld kapseln** -Vorgang ändert sich den Zugriffsmodifizierer für das Feld, das Sie zum kapseln möchten [private](http://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8), und generiert dann [erhalten](http://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)und [festgelegt](http://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) Accessor für das Feld. In einigen Fällen wird nur ein `get`-Accessor generiert, beispielsweise wenn das Feld schreibgeschützt deklariert wird.  
  
 Das Umgestaltungsmodul aktualisiert Ihren Code mit Verweisen auf die neue Eigenschaft in den Bereichen angegeben wird, der **Verweise aktualisieren** Teil der **Feld kapseln** im Dialogfeld.  
  
### <a name="to-create-a-property-from-a-field"></a>So erstellen Sie eine Eigenschaft aus einem Feld  
  
1.  Erstellen Sie eine Konsolenanwendung mit dem Namen `EncapsulateFieldExample`, und ersetzen Sie `Program` durch den folgenden Beispielcode.  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  In der [Code-Editor](../ide/writing-code-in-the-code-and-text-editor.md), platzieren Sie den Cursor in der Deklaration auf den Namen des Felds, das Sie kapseln möchten. Setzen Sie den Cursor im Beispiel unten auf den Begriff `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  Auf der **Umgestalten** Menü klicken Sie auf **Feld kapseln**.  
  
     Die **Feld kapseln** Dialogfeld wird angezeigt.  
  
     Sie können auch die Tastenkombination STRG + R, E anzuzeigende eingeben der **Feld kapseln** Dialogfeld.  
  
     Sie können auch mit der rechten Maustaste des Cursors, zeigen Sie auf **Umgestalten**, und klicken Sie dann auf **Feld kapseln** zum Anzeigen der **Feld kapseln** Dialogfeld.  
  
4.  Geben Sie Einstellungen an.  
  
5.  Drücken Sie die EINGABETASTE, oder klicken Sie auf die **OK** Schaltfläche.  
  
6.  Bei Auswahl der **Vorschau der verweisänderungen** Option, und klicken Sie dann die **Vorschau der Verweisänderungen** Fenster wird geöffnet. Klicken Sie auf die **übernehmen** Schaltfläche.  
  
     Folgender `get`- und `set`-Accessorcode wird in der Quelldatei angezeigt:  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     Der Code in der `Main`-Methode wird ebenfalls auf den neuen Namen der `Width`-Eigenschaften aktualisiert.  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>Hinweise  
 Die **Feld kapseln** Vorgang ist nur möglich, wenn der Cursor in der gleichen Zeile wie die Felddeklaration befindet.  
  
 Für Deklarationen, die mehrere Felder deklariert **Feld kapseln** verwendet das Komma als Trennzeichen zwischen Feldern und initialisiert die Umgestaltung für das Feld, die nächsten zum Cursor befindet und auf derselben Zeile wie der Cursor. Sie können das zu kapselnde Feld auch angeben, indem Sie den Namen des Feldes in der Deklaration auswählen.  
  
 Der durch diesen Umgestaltungsvorgang generierte Code wird durch das Codeausschnittsfeature des Vorgangs „Feld kapseln“ modelliert. Codeausschnitte können geändert werden. Weitere Informationen finden Sie unter [Codeausschnitte](../ide/code-snippets.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)   
 [Visual C#-Codeausschnitte](../ide/visual-csharp-code-snippets.md)
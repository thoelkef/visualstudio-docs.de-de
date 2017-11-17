---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: Umgestaltung (c#) Feld kapseln | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bd9e255b35ffb843c15d5ffa9c1547891bf437d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-field-refactoring-c"></a>Refactoring „Feld kapseln“ (C#)
Die **Feld kapseln** (refactoringvorgang) ermöglicht es Ihnen, schnell eine Eigenschaft aus einem vorhandenen Feld erstellen, und den Code dann nahtlos mit Verweisen auf die neue Eigenschaft zu aktualisieren.  
  
 Wenn eine [Feld](/dotnet/csharp/programming-guide/classes-and-structs/fields) ist [öffentlichen](/dotnet/csharp/language-reference/keywords/public), andere Objekte haben Sie direkten Zugriff auf dieses Feld und ändern können, durch das Objekt, das dieses Feld besitzt unentdeckt bleiben. Mithilfe von [Eigenschaften](/dotnet/csharp/programming-guide/classes-and-structs/properties) zum Kapseln von diesem Felds können Sie direkten Zugriff auf Felder unterbinden.  
  
 Um die neue Eigenschaft erstellen die **Feld kapseln** Vorgang ändert den Zugriffsmodifizierer für das Feld, das Sie zum kapseln möchten [private](/dotnet/csharp/language-reference/keywords/private), und generiert dann [abrufen](/dotnet/csharp/language-reference/keywords/get)und [festgelegt](/dotnet/csharp/language-reference/keywords/set) Accessoren für dieses Feld. In einigen Fällen wird nur ein `get`-Accessor generiert, beispielsweise wenn das Feld schreibgeschützt deklariert wird.  
  
 Die Umgestaltung Engine aktualisiert den Code durch Verweise auf die neue Eigenschaft in den Bereichen, die im angegebenen der **Verweise aktualisieren** Teil der **Feld kapseln** (Dialogfeld).  
  
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
  
2.  In der [Code-Editor](../ide/writing-code-in-the-code-and-text-editor.md), platzieren Sie den Cursor in der Deklaration auf den Namen des Felds, das gekapselt werden soll. Setzen Sie den Cursor im Beispiel unten auf den Begriff `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  Auf der **Umgestalten** Menü klicken Sie auf **Feld kapseln**.  
  
     Die **Feld kapseln** Dialogfeld wird angezeigt.  
  
     Sie können auch die Tastenkombination STRG + R, anzuzeigende eingeben der **Feld kapseln** (Dialogfeld).  
  
     Sie können auch mit der rechten Maustaste des Mauszeiger, zeigen Sie auf **Umgestalten**, und klicken Sie dann auf **Feld kapseln** zum Anzeigen der **Feld kapseln** (Dialogfeld).  
  
4.  Geben Sie Einstellungen an.  
  
5.  Drücken Sie EINGABETASTE, oder klicken Sie auf die **OK** Schaltfläche.  
  
6.  Bei Auswahl der **Verweis Vorschau der Änderungen** Option, und klicken Sie dann die **Verweis Vorschau der Änderungen** Fenster wird geöffnet. Klicken Sie auf die **übernehmen** Schaltfläche.  
  
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
 Die **Feld kapseln** Vorgang ist nur möglich, wenn der Cursor in derselben Zeile wie die Felddeklaration positioniert ist.  
  
 Für Deklarationen, die mehrere Felder deklarieren **Feld kapseln** verwendet das Komma als Trennzeichen zwischen Feldern und initialisiert die Umgestaltung auf das Feld, das am nächsten liegt der Cursor ist und auf derselben Zeile wie der Cursor. Sie können das zu kapselnde Feld auch angeben, indem Sie den Namen des Feldes in der Deklaration auswählen.  
  
 Der durch diesen Umgestaltungsvorgang generierte Code wird durch das Codeausschnittsfeature des Vorgangs „Feld kapseln“ modelliert. Codeausschnitte können geändert werden. Weitere Informationen finden Sie unter [Codeausschnitte](../ide/visual-csharp-code-snippets.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Umgestaltung (c#)](refactoring-csharp.md)   
 [Visual C#-Codeausschnitte](../ide/visual-csharp-code-snippets.md)
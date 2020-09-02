---
title: Refactoring von Feld Kapseln (c#) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667570"
---
# <a name="encapsulate-field-refactoring-c"></a>Refactoring „Feld kapseln“ (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Umgestaltungs Vorgang **Feld kapseln** ermöglicht es Ihnen, schnell eine Eigenschaft aus einem vorhandenen Feld zu erstellen und den Code dann nahtlos mit Verweisen auf die neue Eigenschaft zu aktualisieren.

 Wenn ein [Feld](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) [öffentlich](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e)ist, haben andere Objekte direkten Zugriff auf dieses Feld und können es ändern, was von dem Objekt, das das Feld besitzt, nicht erkannt wird. Wenn Sie das Feld mithilfe von [Eigenschaften](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) Kapseln, können Sie den direkten Zugriff auf Felder nicht zulassen.

 Um die neue Eigenschaft zu erstellen, ändert der Vorgang **Feld kapseln** den Zugriffsmodifizierer für das Feld, das Sie in [Privat](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)Kapseln möchten, und generiert dann [Get](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) -und [Set](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) -Accessoren für dieses Feld. In einigen Fällen wird nur ein `get`-Accessor generiert, beispielsweise wenn das Feld schreibgeschützt deklariert wird.

 Die Refactoring-Engine aktualisiert Ihren Code mit Verweisen auf die neue Eigenschaft in den Bereichen, die im Abschnitt **Update Verweise** des Dialog **Felds Feld kapseln** angegeben sind.

### <a name="to-create-a-property-from-a-field"></a>So erstellen Sie eine Eigenschaft aus einem Feld

1. Erstellen Sie eine Konsolenanwendung mit dem Namen `EncapsulateFieldExample`, und ersetzen Sie `Program` durch den folgenden Beispielcode.

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

2. Platzieren Sie den Cursor im [Code-Editor](../ide/writing-code-in-the-code-and-text-editor.md)in der Deklaration für den Namen des Felds, das Sie kapseln möchten. Setzen Sie den Cursor im Beispiel unten auf den Begriff `width`:

    ```csharp
    public int width, height;
    ```

3. Klicken Sie im Menü **umgestalten** auf **Feld kapseln**.

     Das Dialogfeld **Feld kapseln** wird angezeigt.

     Sie können auch die Tastenkombination STRG + R, E eingeben, um das Dialogfeld **Feld kapseln** anzuzeigen.

     Sie können auch mit der rechten Maustaste auf den Cursor klicken, auf **umgestalten**zeigen und dann auf **Feld kapseln** klicken, um das Dialogfeld **Feld kapseln** anzuzeigen.

4. Geben Sie Einstellungen an.

5. Drücken Sie die EINGABETASTE, oder klicken Sie auf **OK** .

6. Wenn Sie die Option **Vorschau der Verweis Änderungen** ausgewählt haben, wird das Fenster **Vorschau der Verweis Änderungen** geöffnet. Klicken Sie auf die Schaltfläche **Übernehmen**.

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

## <a name="remarks"></a>Bemerkungen
 Der Vorgang zum **Kapseln des Felds** ist nur möglich, wenn sich der Cursor in derselben Zeile wie die Feld Deklaration befindet.

 Für Deklarationen, die mehrere Felder deklarieren, verwendet das **Feld kapseln** das Komma als Begrenzung zwischen Feldern und initiiert das Refactoring für das Feld, das sich am nächsten im Cursor und in derselben Zeile wie der Cursor befindet. Sie können das zu kapselnde Feld auch angeben, indem Sie den Namen des Feldes in der Deklaration auswählen.

 Der durch diesen Umgestaltungsvorgang generierte Code wird durch das Codeausschnittsfeature des Vorgangs „Feld kapseln“ modelliert. Codeausschnitte können geändert werden. Weitere Informationen finden Sie unter [Codeausschnitte](../ide/code-snippets.md).

## <a name="see-also"></a>Weitere Informationen
 [Refactoring (c#)](../csharp-ide/refactoring-csharp.md) [Visual c#-Code Ausschnitte](../ide/visual-csharp-code-snippets.md)
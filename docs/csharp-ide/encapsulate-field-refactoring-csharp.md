---
title: "Encapsulate Field Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.encapsulatefield"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Encapsulate Field refactoring operation [C#]"
  - "refactoring [C#], Encapsulate Field"
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Encapsulate Field Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem Umgestaltungsvorgang **Feld kapseln** können Sie schnell und einfach eine Eigenschaft aus einem vorhandenen Feld erstellen und den Code unmittelbar danach mit Verweisen auf die neue Eigenschaft aktualisieren.  
  
 Wenn ein Feld den Typ [öffentlich](/dotnet/csharp/language-reference/keywords/public) hat, können andere Objekte direkt auf das [Feld](/dotnet/csharp/programming-guide/classes-and-structs/fields) zugreifen und es ändern. Dies bleibt von dem Objekt unbemerkt, das dieses Feld besitzt.  Sie können den Direktzugriff auf Felder verhindern, indem Sie dieses Feld mithilfe von [Eigenschaften](/dotnet/csharp/programming-guide/classes-and-structs/properties) kapseln.  
  
 Um die neue Eigenschaft zu erstellen, wird der Zugriffsmodifizierer des zu kapselnden Felds über den Vorgang **Feld kapseln** in [privat](/dotnet/csharp/language-reference/keywords/private) geändert und anschließend ein [get](/dotnet/csharp/language-reference/keywords/get)\-Accessor und ein [set](/dotnet/csharp/language-reference/keywords/set)\-Accessor für das Feld generiert.  In einigen Fällen wird nur ein `get`\-Accessor generiert, beispielsweise wenn das Feld schreibgeschützt deklariert wird.  
  
 Das Umgestaltungsmodul aktualisiert den Code in den Bereichen, die im Abschnitt **Verweise aktualisieren** des Dialogfelds **Feld kapseln** angegeben sind, mit Verweisen auf die neue Eigenschaft.  
  
### So erstellen Sie eine Eigenschaft aus einem Feld  
  
1.  Erstellen Sie eine Konsolenanwendung mit dem Namen `EncapsulateFieldExample`, und ersetzen Sie `Program` durch den folgenden Beispielcode.  
  
    ```c#  
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
  
2.  Platzieren Sie im [Code\-Editor](../ide/writing-code-in-the-code-and-text-editor.md) den Cursor in der Deklaration auf den Namen des Felds, das Sie kapseln möchten.  Setzen Sie den Cursor im Beispiel unten auf den Begriff `width`:  
  
    ```c#  
    public int width, height;  
    ```  
  
3.  Klicken Sie im Menü **Umgestalten** auf **Feld kapseln**.  
  
     Das Dialogfeld **Feld kapseln** wird angezeigt.  
  
     Sie können auch die Tastenkombination STRG\+R, STRG\+E drücken, um das Dialogfeld **Feld kapseln** anzuzeigen.  
  
     Sie können auch mit der rechten Maustaste klicken, im Kontextmenü auf **Umgestalten** zeigen und dann auf **Feld kapseln** klicken, um das Dialogfeld **Feld kapseln** anzuzeigen.  
  
4.  Geben Sie Einstellungen an.  
  
5.  Drücken Sie die EINGABETASTE, oder klicken Sie auf die Schaltfläche **OK**.  
  
6.  Wenn Sie die Option **Vorschau der Verweisänderungen** aktiviert haben, wird das Fenster **Vorschau der Verweisänderungen** geöffnet.  Klicken Sie auf die Schaltfläche **Übernehmen**.  
  
     Folgender `get`\- und `set`\-Accessorcode wird in der Quelldatei angezeigt:  
  
    ```c#  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     Der Code in der `Main`\-Methode wird ebenfalls auf den neuen Namen der `Width`\-Eigenschaften aktualisiert.  
  
    ```c#  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## Hinweise  
 Der Vorgang **Feld kapseln** kann nur ausgeführt werden, wenn sich der Cursor in derselben Zeile wie die Felddeklaration befindet.  
  
 Bei Deklarationen, in denen mehrere Felder deklariert werden, verwendet **Feld kapseln** das Komma als Trennzeichen zwischen Feldern und initialisiert die Umgestaltung für das Feld, das sich in derselben Zeile und am nächsten zum Cursor befindet.  Sie können das zu kapselnde Feld auch angeben, indem Sie den Namen des Feldes in der Deklaration auswählen.  
  
 Der durch diesen Umgestaltungsvorgang generierte Code wird durch das Codeausschnittsfeature des Vorgangs „Feld kapseln“ modelliert.  Codeausschnitte können geändert werden.  Weitere Informationen finden Sie unter [Codeausschnitte](../ide/code-snippets.md).  
  
## Siehe auch  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)   
 [Visual C\#\-Codeausschnitte](../ide/visual-csharp-code-snippets.md)
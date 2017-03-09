---
title: "Auf &#39;&lt;Methodenname&gt;&#39; kann in diesem Kontext nicht zugegriffen werden, weil auf den R&#252;ckgabetyp nicht zugegriffen werden kann. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36665"
  - "vbc36666"
  - "bc36666"
  - "vbc36665"
helpviewer_keywords: 
  - "BC36666"
  - "BC36666"
ms.assetid: 8f29eb7e-351f-486c-9d1f-3556cc11b7c5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auf &#39;&lt;Methodenname&gt;&#39; kann in diesem Kontext nicht zugegriffen werden, weil auf den R&#252;ckgabetyp nicht zugegriffen werden kann.
Sie haben eine Funktion aufgerufen, die einen Rückgabetyp aufweist, auf den Sie aus der aufrufenden Anweisung nicht zugreifen können. Im folgenden Code tritt z. B. ein Fehler des Aufrufs von `Main` für `PublicMethod` auf, weil der Rückgabetyp \(`PrivateType`\) mit dem `Private`\-Zugriffsmodifizierer in der Klasse `TestClass` deklariert ist. Daher ist der Kontext, in dem auf `PrivateType` zugegriffen werden kann, auf `TestClass` eingeschränkt.  
  
```vb#  
Class TestClass  
  
    Dim pT As New PrivateType  
  
    Private Class PrivateType  
    End Class  
  
    '' A corresponding error is returned in this line: 'PublicMethod   
    '' cannot expose 'PrivateType' in namespace 'ConsoleApplication1'   
    '' through class 'TestClass'.  
    'Public Function PublicMethod() As PrivateType  
    '    Return Nothing  
    'End Function  
  
End Class  
  
Module Module1  
  
    Sub Main()  
  
        Dim tc As TestClass  
        '' This error occurs here, because the data type returned by   
        '' PublicMethod()is declared Private in class TestClass and   
        '' cannot be accessed from here.  
        'Console.WriteLine(tc.PublicMethod())  
  
    End Sub  
  
End Module  
```  
  
 **Fehler\-ID:** BC36665 und BC36666  
  
### So beheben Sie diesen Fehler  
  
-   Wenn auf die Typdefinition zugegriffen werden kann, ändern Sie den Zugriffsmodifizierer aus `Private` in `Public`.  
  
-   Ändern Sie den Rückgabetyp der Funktion, wenn Sie darauf zugreifen können.  
  
-   Schreiben Sie eine Methode oder eine Extensionmethode, die einen Typ zurückgibt, auf den zugegriffen werden kann.  
  
## Siehe auch  
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)
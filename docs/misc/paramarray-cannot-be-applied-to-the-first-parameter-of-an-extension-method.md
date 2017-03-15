---
title: "&quot;ParamArray&quot; kann nicht auf den ersten Parameter einer Erweiterungsmethode angewendet werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36554"
  - "bc36554"
helpviewer_keywords: 
  - "BC36554"
ms.assetid: 0778a854-246f-4c2b-943d-ea8883b3aa6f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;ParamArray&quot; kann nicht auf den ersten Parameter einer Erweiterungsmethode angewendet werden
"ParamArray" kann nicht auf den ersten Parameter einer Erweiterungsmethode angewendet werden. Der erste Parameter gibt den zu erweiternden Typ an.  
  
 Der erste Parameter einer Erweiterungsmethode gibt den Datentyp an, der von der Methode erweitert wird. Daher ist der erste Parameter erforderlich und nicht optional. Ein Parameterarray ist automatisch optional, und daher ist es als erstes Argument einer Erweiterungsmethode unzulässig.  
  
> [!NOTE]
>  Wird die Methode ausgeführt, wird die Instanz des erweiterten Datentyps, der die Methode aufruft, zum Argument für den ersten Parameter der Methode. Beispielsweise ist die Instanz `greeting` in `greeting.Print()` das Argument für den ersten Parameter \(`str`\) in der Erweiterungsmethode `Public Sub Print (ByVal str As String)`.  
  
 **Fehler\-ID:** BC36554  
  
### So beheben Sie diesen Fehler  
  
-   Wenn das Parameterarray den zu erweiternden Datentyp nicht angibt, fügen Sie einen neuen ersten Parameter hinzu, der den Typ angibt.  
  
    ```  
    <Extension()> Public Sub AddTo(ByRef str As String, ByVal ParamArray addOns() As String) ' Concatenate the strings in addOns to str. End Sub  
    ```  
  
-   Wenn das Parameterarray den zu erweiternden Datentyp angibt, können Sie es in ein reguläres Array ändern, das statt eines Parameterarrays ein Argument erfordert. Reguläre Arrays können erweitert werden.  
  
    ```  
    <Extension()> Public Function Sum(ByVal ints() As Integer) As Integer Dim total As Integer = 0 For Each i As Integer In ints total = total + i Next i Return total End Function  
    ```  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)   
 [Optional Parameters](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)
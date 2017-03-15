---
title: "Der Typparameter &lt;Typparametername1&gt; muss entweder eine New-Einschr&#228;nkung oder eine Structure-Einschr&#228;nkung haben, um der New-Einschr&#228;nkung f&#252;r den Typparameter &lt;Typparametername2&gt; zu entsprechen. | Microsoft Docs"
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
  - "vbc32084"
  - "BC32084"
helpviewer_keywords: 
  - "BC32084"
ms.assetid: a7ff58d3-8c67-40e4-9fd8-92cc00524c22
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Typparameter &lt;Typparametername1&gt; muss entweder eine New-Einschr&#228;nkung oder eine Structure-Einschr&#228;nkung haben, um der New-Einschr&#228;nkung f&#252;r den Typparameter &lt;Typparametername2&gt; zu entsprechen.
Eine Anweisung erstellt einen generischen Typ, der einen Typparameter übergibt, der nicht zur Erfüllung der `New`\-Einschränkung beschränkt ist.  
  
 Die `New`\-Einschränkung gibt vor, dass das für den Typparameter angegebene Typargument einen parameterlosen Konstruktor für den Code verfügbar machen muss, der Objekte daraus erstellt. Alle Werttypen verfügen über parameterlose Konstruktoren, jedoch nicht alle Verweistypen. Daher erfüllt die `Structure`\-Einschränkung die `New`\-Einschränkung, aber die `Class`\-Einschränkung bzw. eine Klasse oder ein Schnittstellenname nicht.  
  
 Dieser Fehler kann durch die folgenden Anweisungen generiert werden.  
  
```  
Public Class c1(Of t As New) End Class Public Class c2(Of u) Public testObject As New c1(Of u) End Class  
```  
  
 Wenn die Klasse `c2` ein Objekt aus `c1` erstellt, erfüllt der Typparameter `u` nicht die `New`\-Einschränkung für den Typparameter `t`.  
  
 **Fehler\-ID:** BC32084  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der Typparameter, der dem generischen Typs übergeben werden soll, die `Structure`\- oder `New`\-Einschränkung erfüllen kann, fügen Sie die entsprechende Einschränkung zur Definition hinzu.  
  
    ```  
    Public Class c2(Of u As Structure)  
    ```  
  
-   Wenn der Typparameter die `Structure`\- oder `New`\-Einschränkung nicht erfüllen kann, übergeben Sie ihn nicht an den generischen Typ. Sie müssen ein anderes Element als Typargument übergeben.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/de-de/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Class \(Visual Basic\)](http://msdn.microsoft.com/de-de/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)
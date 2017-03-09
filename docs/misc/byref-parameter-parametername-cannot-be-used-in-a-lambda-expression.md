---
title: "Der &#39;ByRef&#39;-Parameter &#39;&lt;parametername&gt;&#39; kann nicht in einem Lambdaausdruck verwendet werden | Microsoft Docs"
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
  - "bc36639"
  - "vbc36639"
helpviewer_keywords: 
  - "BC36639"
ms.assetid: 5913f9b6-2929-4c05-8dd1-00b10fcd5a83
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der &#39;ByRef&#39;-Parameter &#39;&lt;parametername&gt;&#39; kann nicht in einem Lambdaausdruck verwendet werden
Ein innerhalb einer `Sub` oder Funktion deklarierter Lambdaausdruck kann keine `ByRef`\-Parameter dieser `Sub` oder Funktion verwenden. Beispielsweise verursacht der folgende Code diesen Fehler, da der `ByRef`\-Parameter `n` im Lambdaausdruck verwendet wird.  
  
```  
'' Not valid.   
'Sub ExampleSub(ByRef n As Integer)  
  
'    Dim lambda = Function(p As Integer) p + n  
  
'End Sub  
```  
  
 **Fehler\-ID:** BC36639  
  
### So beheben Sie diesen Fehler  
  
-   Weisen Sie den `ByRef`\-Parameter einer lokalen Variablen zu, und verwenden Sie die lokale Variable im Lambdaausdruck, wie im folgenden Code dargestellt:  
  
    ```  
    Sub ExampleSub(ByRef n As Integer)  
  
        Dim temp = n  
        Dim lambda = Function(p As Integer) p + temp  
  
    End Sub  
    ```  
  
## Siehe auch  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)
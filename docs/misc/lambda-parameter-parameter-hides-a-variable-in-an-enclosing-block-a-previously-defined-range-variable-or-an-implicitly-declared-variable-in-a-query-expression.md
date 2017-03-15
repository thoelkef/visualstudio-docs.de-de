---
title: "Der lambda-Parameter &#39;&lt;Parameter&gt;&#39; verbirgt eine Variable in einem einschlie&#223;enden Block, eine zuvor definierte Bereichsvariable oder eine implizit im Abfrageausdruck deklarierte Variable. | Microsoft Docs"
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
  - "bc36641"
  - "vbc36641"
helpviewer_keywords: 
  - "BC36641"
ms.assetid: ee08c366-29d1-4abb-b14c-23ae2b9680e7
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der lambda-Parameter &#39;&lt;Parameter&gt;&#39; verbirgt eine Variable in einem einschlie&#223;enden Block, eine zuvor definierte Bereichsvariable oder eine implizit im Abfrageausdruck deklarierte Variable.
Eine Variable in einem Lambdaausdruck weist denselben Namen wie eine zuvor im gleichen Gültigkeitsbereich definierte Variable auf. Dies kann eine Variable in einem einschließenden Codeblock für einen geschachtelten Lambdaausdruck, eine zuvor in einer LINQ\-Abfrage definierte Bereichsvariable oder eine Variable sein, die implizit für eine LINQ\-Abfrage deklariert wird.  
  
 **Fehler\-ID:** BC36641  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass alle Variablen im Lambdaausdruck über eindeutige Namen verfügen, die im selben Bereich nicht doppelt vorkommen.  
  
## Siehe auch  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)
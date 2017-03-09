---
title: "Die Variable kann nicht mit einem &#39;&lt;elementname&gt;&#39; initialisiert werden, der kein Arraytyp ist. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36536"
  - "bc36536"
helpviewer_keywords: 
  - "BC36536"
ms.assetid: 959415de-164e-4971-aab0-faad315753e9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Variable kann nicht mit einem &#39;&lt;elementname&gt;&#39; initialisiert werden, der kein Arraytyp ist.
Eine Variable, die als Array deklariert ist, muss mit einem Arraywert initialisiert werden.  
  
```  
' Not valid. ' The following line causes this error when executed with Option Strict off. ' Dim arrayVar1() = 10  
```  
  
 **Fehler\-ID:** BC36536  
  
### So beheben Sie diesen Fehler  
  
-   Initialisieren Sie die Arrayvariable mit einem Arraywert:  
  
    ```  
    ' With Option Strict off. Dim arrayVar2() = {1, 2, 3} ' With Option Strict on. Dim arrayVar3() As Integer = {1, 2, 3}  
    ```  
  
## Siehe auch  
 [NICHT IM BUILD: Arrayvariable](http://msdn.microsoft.com/de-de/c2da78bd-6928-46ba-805f-44f819dfaf93)
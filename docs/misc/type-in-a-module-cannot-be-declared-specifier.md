---
title: "Ein Typ in einem Modul kann nicht als &#39;&lt;bezeichner&gt;&#39; deklariert werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30735"
  - "bc30735"
helpviewer_keywords: 
  - "BC30735"
ms.assetid: df94d581-7f5b-4d42-ae2b-1ef912f133cc
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein Typ in einem Modul kann nicht als &#39;&lt;bezeichner&gt;&#39; deklariert werden
Ein Typ mit ungültigen Modifizierern wurde in einem Modul deklariert.  
  
 **Fehler\-ID:** BC30735  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie nicht die Modifizierer `Protected` oder `Protected Friend` für Typen, die innerhalb eines Moduls deklariert werden.  
  
## Siehe auch  
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)
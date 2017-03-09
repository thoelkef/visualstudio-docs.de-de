---
title: "&#39;&lt;Membername&gt;&#39; ist in mehreren Basisschnittstellen vorhanden. | Microsoft Docs"
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
  - "vbc31040"
  - "bc31040"
helpviewer_keywords: 
  - "BC31040"
ms.assetid: c1a80d64-3986-417f-af92-412183e490ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Membername&gt;&#39; ist in mehreren Basisschnittstellen vorhanden.
'\<Membername\>' ist in mehreren Basisschnittstellen vorhanden. Verwenden Sie den Namen der Schnittstelle, die '\<Membername\>' in der Implements\-Klausel deklariert, und nicht den Namen der abgeleiteten Schnittstelle.  
  
 Diese Schnittstelle erbt Member mit demselben Namen von mehreren Schnittstellen, was zur Mehrdeutigkeit führt.  
  
 **Fehler\-ID:** BC31040  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie den definierenden Schnittstellennamen in den `Implements`\-Klauseln anstelle des Namens der abgeleiteten Schnittstelle.  
  
## Siehe auch  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)
---
title: "Das Schl&#252;sselwort &quot;&lt;Schl&#252;sselwort&gt;&quot; wird zum &#220;berladen von geerbten Membern verwendet. Verwenden Sie das Schl&#252;sselwort &quot;&lt;Schl&#252;sselwort&gt;&quot; nicht beim &#220;berladen von &quot;Sub New&quot; | Microsoft Docs"
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
  - "vbc32040"
  - "bc32040"
helpviewer_keywords: 
  - "BC32040"
ms.assetid: 39e6ee0d-b8a0-498e-bdaf-a4ceb13892fe
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Schl&#252;sselwort &quot;&lt;Schl&#252;sselwort&gt;&quot; wird zum &#220;berladen von geerbten Membern verwendet. Verwenden Sie das Schl&#252;sselwort &quot;&lt;Schl&#252;sselwort&gt;&quot; nicht beim &#220;berladen von &quot;Sub New&quot;
Ein Konstruktor wird mit dem `Overloads`\-Schlüsselwort deklariert.  
  
 Visual Basic unterstützt nicht das Vererben oder Überladen von Konstruktoren.  
  
 **Fehler\-ID:** BC32040  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Overloads`\-Schlüsselwort aus allen Konstruktordeklarationen.  
  
## Siehe auch  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)
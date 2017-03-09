---
title: "Der &#39;&lt;Konstruktor&gt;&#39; in dem vom Designer generierten Typ &#39;&lt;Typ&gt;&#39; sollte eine InitializeComponent-Methode aufrufen. | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40054"
  - "bc40054"
helpviewer_keywords: 
  - "BC40054"
ms.assetid: beac93b0-d427-4df6-9582-fd69c7a53673
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der &#39;&lt;Konstruktor&gt;&#39; in dem vom Designer generierten Typ &#39;&lt;Typ&gt;&#39; sollte eine InitializeComponent-Methode aufrufen.
Ein Konstruktor in einem vom Designer generierten Typ ruft nicht die `InitializeComponent`\-Methode des Typs auf.  
  
 Jeder Konstruktor in einem vom Designer generierten Typ muss die `InitializeComponent`\-Methode des Typs aufrufen.  
  
 **Fehler\-ID:** BC40054  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie einen Aufruf der `InitializeComponent`\-Methode im Konstruktor hinzu.  
  
## Siehe auch  
 <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute>   
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)
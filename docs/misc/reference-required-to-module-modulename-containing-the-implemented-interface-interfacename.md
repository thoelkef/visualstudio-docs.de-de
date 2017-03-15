---
title: "Es ist ein Verweis auf das Modul &#39;&lt;modulname&gt;&#39; erforderlich, das die implementierte Schnittstelle &#39;&lt;schnittstellenname&gt;&#39; enth&#228;lt | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30010"
  - "bc30010"
helpviewer_keywords: 
  - "BC30010"
ms.assetid: 57fe7e15-bf99-49d1-ba6c-bb7abeb615b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es ist ein Verweis auf das Modul &#39;&lt;modulname&gt;&#39; erforderlich, das die implementierte Schnittstelle &#39;&lt;schnittstellenname&gt;&#39; enth&#228;lt
Es ist ein Verweis auf das Modul '\<modulname\>' erforderlich, das die implementierte Schnittstelle '\<schnittstellenname\>' enthält. Fügen Sie dem Projekt einen Verweis hinzu.  
  
 Die Schnittstelle ist in einem Modul definiert, auf das Ihr Projekt nicht direkt verweist. Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler benötigt einen Verweis, um Mehrdeutigkeiten zu vermeiden, falls die Schnittstelle in mehr als einem Modul definiert ist.  
  
 **Fehler\-ID:** BC30010  
  
### So beheben Sie diesen Fehler  
  
-   Nehmen Sie den Namen des nicht referenzierten Moduls in Ihre Projektverweise auf.  
  
## Siehe auch  
 [NICHT IM BUILD: Verweisen auf Namespaces und Komponenten](http://msdn.microsoft.com/de-de/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)
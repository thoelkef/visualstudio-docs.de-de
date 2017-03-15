---
title: "Verweis auf das Modul &#39;&lt;Modulname&gt;&#39; mit der Basisklasse &#39;&lt;Klassenname&gt;&#39; erforderlich. | Microsoft Docs"
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
  - "vbc30008"
  - "bc30008"
helpviewer_keywords: 
  - "BC30008"
ms.assetid: ec8de475-8a8b-4aa5-86c9-6fcc44dcec06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Verweis auf das Modul &#39;&lt;Modulname&gt;&#39; mit der Basisklasse &#39;&lt;Klassenname&gt;&#39; erforderlich.
Verweis auf das Modul '\<Modulname\>' mit der Basisklasse '\<Klassenname\>' erforderlich. Fügen Sie dem Projekt einen Verweis hinzu.  
  
 Die Klasse ist in einem Modul definiert, auf das Ihr Projekt nicht direkt verweist. Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler benötigt einen Verweis, um Mehrdeutigkeiten zu vermeiden, falls die Klasse in mehr als einem Modul definiert ist.  
  
 **Fehler\-ID:** BC30008  
  
### So beheben Sie diesen Fehler  
  
-   Nehmen Sie den Namen des nicht referenzierten Moduls in Ihre Projektverweise auf.  
  
## Siehe auch  
 [NIB: Verweisen auf Namespaces und Komponenten](http://msdn.microsoft.com/de-de/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)
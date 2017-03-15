---
title: "&lt;Elementname&gt; verweist auf Typ &lt;Typname&gt; in Projekt &lt;Projektname&gt;, Typ &lt;Typname&gt; wurde jedoch in Projekt &lt;Projektname&gt; nicht gefunden. | Microsoft Docs"
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
  - "vbc30960"
  - "bc30960"
helpviewer_keywords: 
  - "BC30960"
ms.assetid: 4ed4bff5-c670-46f6-8360-7287444d50e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Elementname&gt; verweist auf Typ &lt;Typname&gt; in Projekt &lt;Projektname&gt;, Typ &lt;Typname&gt; wurde jedoch in Projekt &lt;Projektname&gt; nicht gefunden.
Ein Ausdruck greift auf eine Klasse, eine Struktur, ein Modul oder eine Schnittstelle zu, auf die in einem anderen Projekt verwiesen wird, dieses Projekt enthält aber nicht den angegebenen Typ.  
  
 Dieser Fehler tritt auf, wenn Ihr Projekt einen indirekten Verweis auf ein anderes Projekt in der gleichen Projektmappe enthält. In der Regel verweist das Projekt auf eine Assembly, die einen Verweis auf das andere Projekt enthält. Wenn die Assembly auf den angegebene Typ in dem anderen Projekt zugreift, wird der indirekte Verweis auf den Typ hergestellt. Wenn der Typ in dem anderen Projekt aber nicht vorhanden ist, wird dieser Fehler generiert.  
  
 **Fehler\-ID:** BC30960  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der angegebene Typ an keiner Stelle mehr definiert ist, entfernen oder ersetzen Sie die Anweisung, die versucht, darauf zuzugreifen. Sie müssen die gleiche Änderung möglicherweise auch in der Assembly vornehmen, die den indirekten Verweis auf den genannten Typ bereitstellt.  
  
-   Wenn der genannte Typ an anderer Stelle definiert ist, verweisen Sie direkt auf das Projekt oder die Assembly, die ihn definiert.  
  
## Siehe auch  
 [NICHT IM BUILD: Verweisen auf Namespaces und Komponenten](http://msdn.microsoft.com/de-de/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [NIB: Verwalten von Verweisen](http://msdn.microsoft.com/de-de/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
---
title: "Das Konstrukt verweist indirekt auf das Projekt &#39;&lt;Projektname&gt;&#39;, das &#39;&lt;Typname&gt;&#39; enth&#228;lt. | Microsoft Docs"
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
  - "vbc31533"
  - "bc31533"
helpviewer_keywords: 
  - "BC31533"
ms.assetid: e3f55f9f-92be-4ecb-bc8f-9e57049a0805
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Konstrukt verweist indirekt auf das Projekt &#39;&lt;Projektname&gt;&#39;, das &#39;&lt;Typname&gt;&#39; enth&#228;lt.
Das Konstrukt verweist indirekt auf das Projekt '\<Projektname\>', das '\<Typname\>' enthält. Fügen Sie Ihrem Projekt einen Projektverweis auf '\<Projektname\>' hinzu.  
  
 Ein Ausdruck oder eine Anweisung greift auf einen Typ zu, der in einem anderen Projekt definiert ist, aber Ihr Projekt verweist nicht direkt auf das definierende Projekt.  
  
 Der Typ kann eine Klasse, eine Struktur, eine Schnittstelle, ein Modul oder eine Enumeration sein.  
  
 Das Projekt, das den genannten Typ definiert, erzeugt eine Assembly, die den Typ enthält. Wenn Ihr Projekt nicht direkt auf das definierende Projekt verweist, kann der Compiler nicht garantieren, dass die Assembly mit dem Typ in der Lösung vorhanden und für den Zugriff verfügbar ist.  
  
 **Fehler\-ID:** BC31533  
  
### So beheben Sie diesen Fehler  
  
-   Bestimmen Sie, welches Projekt den genannten Typ definiert, und fügen Sie einen Projektverweis darauf hinzu.  
  
## Siehe auch  
 [NIB: Verweisen auf Namespaces und Komponenten](http://msdn.microsoft.com/de-de/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [NIB: Verwalten von Verweisen](http://msdn.microsoft.com/de-de/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
---
title: "In Strukturen deklarierte Methoden k&#246;nnen keine Handles-Klauseln haben. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30728"
  - "bc30728"
helpviewer_keywords: 
  - "BC30728"
ms.assetid: 64c70bb5-3696-4865-8194-328394c2b4b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# In Strukturen deklarierte Methoden k&#246;nnen keine Handles-Klauseln haben.
Strukturmethoden können das `Handles`\-Schlüsselwort nicht zum Behandeln von Ereignissen verwenden.  
  
 **Fehler\-ID:** BC30728  
  
### So beheben Sie diesen Fehler  
  
-   Sie sollten einen Neuentwurf Ihrer Struktur als Klasse in Erwägung ziehen.  
  
     Sie können `AddHandler` verwenden, um ein Ereignis mit einem Ereignishandler in einer Struktur zu verknüpfen, vorausgesetzt, die Struktur implementiert einen in einer Schnittstelle definierten Ereignishandler.  
  
## Siehe auch  
 [Structures and Classes](/dotnet/visual-basic/programming-guide/language-features/data-types/structures-and-classes)   
 [NICHT IM BUILD: Klassen: Blaupausen für Objekte](http://msdn.microsoft.com/de-de/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)   
 [NICHT IM BUILD: AddHandler und RemoveHandler](http://msdn.microsoft.com/de-de/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)
---
title: "System.Runtime.InteropServices.DllImportAttribute kann nicht auf die AddHandler-, RemoveHandler- oder RaiseEvent-Methode angewendet werden. | Microsoft Docs"
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
  - "bc31531"
  - "vbc31531"
helpviewer_keywords: 
  - "BC31531"
ms.assetid: 0ea3a16c-cfe0-4cb5-b740-358679272f8d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Runtime.InteropServices.DllImportAttribute kann nicht auf die AddHandler-, RemoveHandler- oder RaiseEvent-Methode angewendet werden.
Das `DllImportAttribute`\-Attribut wurde auf eine `AddHandler`\-, `RemoveHandler`\- oder `RaiseEvent`\-Methodendeklaration angewendet. Dieses Attribut kann nur verwendet werden, wenn `Function` oder `Sub` leer ist.  
  
 **Fehler\-ID:** BC31531  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `DllImportAttribute`\-Attribut aus der Methodendeklaration.  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- löschen](http://msdn.microsoft.com/de-de/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- löschen](http://msdn.microsoft.com/de-de/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- löschen](http://msdn.microsoft.com/de-de/7f765da0-5491-40b6-9ed5-24c98f9daad9)
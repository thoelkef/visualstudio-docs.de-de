---
title: "Durch die Anweisung wird der enthaltende AddHandler f&#252;r das Ereignis &quot;&lt;Ereignisname&gt;&quot; rekursiv aufgerufen. | Microsoft Docs"
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
  - "bc41998"
  - "vbc41998"
helpviewer_keywords: 
  - "BC41998"
ms.assetid: 4375b191-fbd9-4e93-b9bb-9159d533ddf6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Durch die Anweisung wird der enthaltende AddHandler f&#252;r das Ereignis &quot;&lt;Ereignisname&gt;&quot; rekursiv aufgerufen.
Die Anweisungen im `AddHandler`\-Accessor einer Ereignisdefinition dürfen nicht direkt auf das Ereignis verweisen.  
  
 Es wird empfohlen, die Liste der Ereignishandler als privates Feld in der Klasse, der Struktur oder dem Modul zu speichern, die bzw. das das Ereignis definiert. Weitere Informationen finden Sie unter [How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md) und [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md).  
  
 **Fehler\-ID:** BC41998  
  
### So beheben Sie diesen Fehler  
  
-   Schreiben Sie die Ereignisdefinition neu, um Rekursion zu vermeiden.  
  
## Siehe auch  
 [AddHandler \- löschen](http://msdn.microsoft.com/de-de/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)
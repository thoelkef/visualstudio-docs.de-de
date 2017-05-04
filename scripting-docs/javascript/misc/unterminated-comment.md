---
title: "Nicht abgeschlossener Kommentar | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Nicht abgeschlossener Kommentar
Sie haben einen mehrzeiligen Kommentarblock begonnen, jedoch nicht ordnungsgemäß abgeschlossen.  Mehrzeilige Kommentare müssen mit der Kombination "\/\*" beginnen und mit der umgekehrten Kombination "\*\/" abgeschlossen werden.  Im Folgenden finden Sie ein Beispiel dazu:  
  
```javascript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### So beheben Sie diesen Fehler  
  
-   Schließen Sie mehrzeilige Kommentare immer mit "\*\/" ab.  
  
## Siehe auch  
 [Comment\-Anweisungen](../../javascript/reference/comment-statements-javascript.md)
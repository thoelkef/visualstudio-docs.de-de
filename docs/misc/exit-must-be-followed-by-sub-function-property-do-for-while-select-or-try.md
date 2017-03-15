---
title: "Auf &#39;Exit&#39; muss &#39;Sub&#39;, &#39;Function&#39;, &#39;Property&#39;, &#39;Do&#39;, &#39;For&#39;, &#39;While&#39;, &#39;Select&#39; oder &#39;Try&#39; folgen. | Microsoft Docs"
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
  - "bc30240"
  - "vbc30240"
helpviewer_keywords: 
  - "BC30240"
ms.assetid: 91078689-f4bf-4331-a475-10bc9fe7cd0c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auf &#39;Exit&#39; muss &#39;Sub&#39;, &#39;Function&#39;, &#39;Property&#39;, &#39;Do&#39;, &#39;For&#39;, &#39;While&#39;, &#39;Select&#39; oder &#39;Try&#39; folgen.
Eine `Exit`\-Anweisung enthält ein ungültiges Schlüsselwort.`Exit` muss den Block angeben, von dem die Steuerung an die auf den Block folgende Anweisung übergeben werden soll, z. B. `End While`.  
  
 **Fehler\-ID:** BC30240  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie ein gültiges Schlüsselwort im Anschluss an `Exit` hinzu, oder entfernen Sie die `Exit`\-Anweisung.  
  
## Siehe auch  
 [Exit Statement](/dotnet/visual-basic/language-reference/statements/exit-statement)
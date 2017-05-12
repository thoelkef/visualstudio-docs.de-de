---
title: "&quot;)&quot; erwartet (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1006"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2fb72012-0f83-40fa-b747-167940d90bdd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# &quot;)&quot; erwartet (JavaScript)
Sie haben versucht, einen Ausdruck in einem Satz von Klammern einzuschließen, Sie haben jedoch die schließende Klammer nicht einbezogen.  Einige Ausdrücke müssen innerhalb von öffnenden und schließenden Klammer eingeschlossen werden.  Beachten Sie die Verwendung von Klammern im folgenden Beispiel.  
  
```javascript  
for (initialize; test; increment) {  
statement;  
}  
```  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie die rechten Klammern dem Auswertungsausdruck hinzu.
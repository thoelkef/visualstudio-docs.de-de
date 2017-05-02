---
title: "&quot;@&quot; erwartet | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1032"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# &quot;@&quot; erwartet
Sie haben versucht, mithilfe der `@set`\-Anweisung eine Variable für die Verwendung mit bedingten Kompilierungsanweisungen zu erstellen, haben dem Variablennamen aber kein "**@**" vorangestellt.  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie das Zeichen "**@**" direkt vor dem Variablennamen ein.  Beispiel:  
  
    ```javascript  
    @set @myvar = 1  
    ```  
  
## Siehe auch  
 [@set\-Anweisung](../../javascript/reference/at-set-statement-javascript.md)   
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)
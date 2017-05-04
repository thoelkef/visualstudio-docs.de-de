---
title: "Hexadezimalzahl erwartet | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Hexadezimalzahl erwartet
Sie haben eine falsche Unicode\-Escapesequenz erstellt.  Unicode\-Escapesequenzen beginnen mit \\u, gefolgt von genau vier Hexadezimalzahlen \(nicht mehr und nicht weniger\).  Unicode\-Hexadezimalziffern können nur die Zahlen 0 bis 9 enthalten, die Großbuchstaben A bis F und die Kleinbuchstaben a bis f.  Das folgende Beispiel veranschaulicht eine ordnungsgemäß gebildete Unicode\-Escapesequenz.  
  
```javascript  
z = "\u1A5F";  
```  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die Unicode\-Hexadezimalziffern mit \\u beginnen, nur die Zahlen 0 bis 9, die Großbuchstaben A bis F und die Kleinbuchstaben a bis f enthalten und zu jeweils vier Ziffern gruppiert sind.  
  
    > [!NOTE]
    >  Wenn Sie den Literaltext \\u in einer Zeichenfolge verwenden möchten, geben Sie zwei umgekehrte Schrägstriche \(\\\\u\) an, wobei der erste umgekehrte Schrägstrich als Escapezeichen für den zweiten umgekehrten Schrägstrich fungiert.  
  
## Siehe auch  
 [Datentypen](../../javascript/data-types-javascript.md)
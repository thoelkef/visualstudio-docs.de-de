---
title: "toGMTString-Methode (Datum) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "toGMTString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toGMTString-Methode"
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toGMTString-Methode (Datum) (JavaScript)
Gibt ein Datum zurück, das unter Verwendung der GMT \(Greenwich Mean Time\) in eine Zeichenfolge konvertiert wurde.  
  
## Syntax  
  
```  
  
dateObj.toGMTString()   
```  
  
## Hinweise  
 Der erforderliche `dateObj`\-Verweis ist ein beliebiges `Date`\-Objekt.  
  
 Die `toGMTString`\-Methode ist veraltet und wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.  Es wird empfohlen, stattdessen die `toUTCString`\-Methode zu verwenden.  
  
 Die `toGMTString`\-Methode gibt ein `String`\-Objekt im Format der GMT\-Konvention zurück.  Der Rückgabewert hat folgendes Format: "5. Januar 1996 00:00: 00 GMT".  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [toUTCString\-Methode \(Datum\)](../../javascript/reference/toutcstring-method-date-javascript.md)
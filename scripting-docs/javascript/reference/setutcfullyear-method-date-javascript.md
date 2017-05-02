---
title: "setUTCFullYear-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, UTC"
  - "setUTCFullYear-Methode"
  - "UTC-Datumsangaben, Festlegen"
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCFullYear-Methode (Datum) (JavaScript)
Legt den Wert des Jahres im `Date`\-Objekt unter Verwendung von UTC \(Universal Time Coordinated, koordinierte Weltzeit\) fest.  
  
## Syntax  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 `numYear`  
 Erforderlich.  Ein dem Jahr entsprechender numerischer Wert.  
  
 `numMonth`  
 Optional.  Ein dem Monat entsprechender numerischer Wert.  Januar hat den Wert 0, und die nachfolgenden Werte geben die weiteren Monate an.  Muss angegeben werden, wenn *numDate* angegeben wird.  
  
 *numDate*  
 Optional.  Ein dem Tag des Monats entsprechender numerischer Wert.  
  
## Hinweise  
 Alle **set**\-Methoden, denen optionale Argumente übergeben werden, verwenden den von den entsprechenden **get**\-Methoden zurückgegebenen Wert, wenn kein optionales Argument angegeben wurde.  Wenn beispielsweise das `numMonth`\-Argument nicht angegeben wird, verwendet [!INCLUDE[javascript](../../includes/javascript-md.md)] den Wert, der von der `getUTCMonth`\-Methode zurückgegeben wird.  
  
 Wenn darüber hinaus der Wert eines Arguments größer als dessen Bereich oder eine negative Zahl ist, werden andere gespeicherte Werte entsprechend geändert.  
  
 Um das Jahr unter Verwendung der Ortszeit festzulegen, verwenden Sie die `setFullYear`\-Methode.  
  
 Der Bereich der im `Date`\-Objekt unterstützten Jahre beträgt etwa 285.616 Jahre in beide Richtungen ab 1970.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCFullYear`\-Methode veranschaulicht.  
  
```javascript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getFullYear\-Methode \(Datum\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear\-Methode \(Datum\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear\-Methode \(Datum\)](../../javascript/reference/setfullyear-method-date-javascript.md)
---
title: "setYear-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "setYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setYear-Methode"
  - "Year-Methode"
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# setYear-Methode (Datum) (JavaScript)
Legt den Wert des Jahres im `Date`\-Objekt fest.  
  
## Syntax  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## Parameter  
 `dateObj`  
 Erforderlich.  Ein beliebiges `Date`\-Objekt.  
  
 `numYear`  
 Erforderlich.  Für die Jahre 1900 bis 1999 ist dies ein numerischer Wert, der dem Jahr minus 1900 entspricht.  Für Datumsangaben außerhalb dieses Bereichs ist dies ein vierstelliger numerischer Wert.  
  
## Hinweise  
 Diese Methode ist veraltet und wird nur für die Abwärtskompatibilität bereitgestellt.  Verwenden Sie stattdessen die `setFullYear`\-Methode.  
  
 Um die Jahreszahl eines `Date`\-Objekts auf 1997 festzulegen, verwenden Sie den Aufruf **setYear\(97\)**.  Um die Jahreszahl auf 2010 festzulegen, verwenden Sie den Aufruf **setYear\(2010\)**.  Um das Jahr auf einen Bereich von 0 bis 99 festzulegen, verwenden Sie die `setFullYear`\-Methode.  
  
> [!NOTE]
>  Bei [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Version 1.0 verwendet `setYear` einen Wert, der sich aus der Addition von 1900 und der Jahreszahl ergibt, die von `numYear` bereitgestellt wird. Dabei ist die Jahreszahl nicht relevant.  Wenn Sie z. B. das Jahr 1899 festlegen möchten, ist `numYear` \-1. Wenn Sie das Jahr 2000 festlegen möchten, entspricht `numYear` 100.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getFullYear\-Methode \(Datum\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear\-Methode \(Datum\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear\-Methode \(Datum\)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear\-Methode \(Datum\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear\-Methode \(Datum\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)
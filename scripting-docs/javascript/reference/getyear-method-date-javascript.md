---
title: "getYear-Methode (Datum) (JavaScript) | Microsoft Docs"
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
  - "getYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Datumsangaben, Zurückgeben des Jahres"
  - "GetYear-Methode"
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# getYear-Methode (Datum) (JavaScript)
Ruft das Jahr eines `Date`\-Objekts ab.  
  
## Syntax  
  
```  
  
dateObj.getYear()   
```  
  
#### Parameter  
 Der erforderliche `dateObj` Verweis ist ein `Date`\-Objekt.  
  
## Rückgabewert  
 Gibt das Jahr zurück.  
  
## Hinweise  
  
> [!IMPORTANT]
>  Diese Methode ist veraltet und wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.  Verwenden Sie stattdessen die `getFullYear`\-Methode.  
  
 In [!INCLUDE[jsv1textspecific](../../includes/jsv1textspecific-md.md)] und dann in Internet Explorer\-Versionen, die mit [!INCLUDE[jsv9textspecific](../../includes/jsv9textspecific-md.md)] beginnen, ist der zurückgegebene Wert das gespeicherte Jahr minus 1900.  Das Jahr 1899 wird z. B. als \-1 und das Jahr 2000 als 100 zurückgegeben.  
  
 In [!INCLUDE[jsv3textspecific](../../includes/jsv3textspecific-md.md)] durch [!INCLUDE[jsv58textspecific](../../includes/jsv58textspecific-md.md)], hängt die Formel im Jahr ab.  Während der Jahre 1900 bis 1999, ist der zurückgegebene Wert ein zweistelliger Wert, der das gespeicherte Jahr minus 1900 ist.  Für Datumsangabenaußenseite, das der Fensterbereich, wird die vierstellige Jahreszahl zurückgegeben.  Beispielsweise wird 1996 als 96 zurückgegeben, aber 1825 und 2025 werden zurückgegeben, wie ist.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [getFullYear\-Methode \(Datum\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear\-Methode \(Datum\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear\-Methode \(Datum\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear\-Methode \(Datum\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear\-Methode \(Datum\)](../../javascript/reference/setyear-method-date-javascript.md)
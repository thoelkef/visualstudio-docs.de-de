---
title: "toLocaleString-Methode (Objekt) (JavaScript) | Microsoft Docs"
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
  - "toLocaleString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleString-Methode"
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toLocaleString-Methode (Objekt) (JavaScript)
Gibt ein Datum zurück, das unter Verwendung des aktuellen Gebietsschemas in eine Zeichenfolge konvertiert wurde.  
  
## Syntax  
  
```  
  
dateObj.toLocaleString()   
```  
  
## Hinweise  
 Das erforderliche `dateObj` ist ein beliebiges `Date`\-Objekt.  
  
 Die `toLocaleString`\-Methode gibt ein `String`\-Objekt zurück, in dem das Datum im langen Standardformat des aktuellen Gebietsschemas enthalten ist.  
  
-   Daten zwischen 1601 und 1999 werden entsprechend den regionalen Einstellungen des Benutzers in der Systemsteuerung formatiert.  
  
-   Für Daten außerhalb dieses Zeitraums wird das Standardformat der **toString**\-Methode verwendet.  
  
 Beispielsweise gibt `toLocaleString` in den USA für den 5. Januar "01\/05\/96 00:00:00" zurück.  In Europa wird für dasselbe Datum "05\/01\/96 00:00:00" zurückgegeben, da der Tag im europäischen Gebrauch vor dem Monat angegeben wird.  
  
> [!NOTE]
>  `toLocaleString` sollte nur zum Anzeigen der Ergebnisse für den Benutzer verwendet werden und nie als Grundlage zur Berechnung in einem Skript, da das zurückgegebene Ergebnis computerspezifisch ist.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `toLocaleString`\-Methode veranschaulicht.  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Array\-Objekt](../../javascript/reference/array-object-javascript.md)&#124; [Date\-Objekt](../../javascript/reference/date-object-javascript.md)&#124; [Number\-Objekt](../../javascript/reference/number-object-javascript.md)&#124; [Object\-Objekt](../../javascript/reference/object-object-javascript.md)  
  
## Siehe auch  
 [toLocaleDateString\-Methode \(Datum\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)
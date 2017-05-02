---
title: "number-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs"
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
  - "Number"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number-Eigenschaft"
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# number-Eigenschaft (Fehler) (JavaScript)
Gibt den numerischen Wert zurück, der einem bestimmten Fehler zugeordnet ist, bzw. legt diesen fest.  Die Standardeigenschaft des `Error`\-Objekts ist **number**.  
  
## Syntax  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## Parameter  
 *Object*  
 Beliebige Instanz des `Error`\-Objekts.  
  
 *errorNumber*  
 Eine ganze Zahl, die einen Fehler darstellt.  
  
## Hinweise  
 Eine Fehlernummer ist ein 32\-Bit\-Wert.  Der obere Teil des 16\-Bit\-Werts ist der Bereichscode, und der untere Teil stellt den Fehlercode dar.  Um den tatsächlichen Fehlercode zu ermitteln, kombinieren Sie die number\-Eigenschaft unter Verwendung des Operators `&` \(bitweises AND\) mit der Hexadezimalzahl `0xFFFF`.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Ausnahme ausgelöst und der aus der Fehlernummer abgeleitete Fehlercode angezeigt.  
  
```javascript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## Beispiel  
 Dieser Code generiert die folgende Ausgabe.  
  
```javascript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Gilt für**: [Error\-Objekt](../../javascript/reference/error-object-javascript.md)  
  
## Siehe auch  
 [description\-Eigenschaft \(Fehler\)](../../javascript/reference/description-property-error-javascript.md)   
 [message\-Eigenschaft \(Fehler\)](../../javascript/reference/message-property-error-javascript.md)   
 [name\-Eigenschaft \(Fehler\)](../../javascript/reference/name-property-error-javascript.md)
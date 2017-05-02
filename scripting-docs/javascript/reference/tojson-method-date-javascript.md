---
title: "toJSON-Methode (Datum) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toJSON-Methode"
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# toJSON-Methode (Datum) (JavaScript)
Wird von der [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)\-Methode verwendet, um die Transformation der Daten eines Objekts für die JSON\-Serialisierung \(JavaScript Object Notation\) zu aktivieren.  
  
## Syntax  
  
```  
  
objectname.toJSON()  
```  
  
## Parameter  
 `objectname`  
 Erforderlich.  Ein Objekt, für das JSON\-Serialisierung erforderlich ist.  
  
## Hinweise  
 Die `toJSON`\-Methode wird von der `JSON.stringify`\-Funktion verwendet.  `JSON.stringify` serialisiert einen [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Wert in JSON\-Text.  Wenn eine `toJSON`\-Methode für `JSON.stringify` bereitgestellt wird, wird die `toJSON`\-Methode aufgerufen, wenn `JSON.stringify` aufgerufen wird.  
  
 Die `toJSON`\-Methode ist ein integrierter Member des [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekts [Date](../../javascript/reference/date-object-javascript.md) Sie gibt eine ISO\-formatierte Datumszeichenfolge für die UTC\-Zeitzone zurück \(gekennzeichnet durch das Suffix Z\).  
  
 Sie können die `toJSON`\-Methode für den `Date`\-Typ überschreiben, oder eine `toJSON`\-Methode für andere Objekttypen definieren, um die Daten eines bestimmten Objekttyps vor der JSON\-Serialisierung zu transformieren.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie mit der `toJSON`\-Methode Zeichenfolgenmemberwerte in Großbuchstaben serialisiert werden.  Diese `toJSON`\-Methode wird beim Aufruf der `JSON.stringify`\-Methode aufgerufen.  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt die Verwendung der `toJSON`\-Methode, die ein integrierter Member des [Date](../../javascript/reference/date-object-javascript.md)\-Objekts ist.  
  
```javascript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## Anforderungen  
 [!INCLUDE[jsv58](../../includes/jsv58-md.md)] **Gilt für:** [Date\-Objekt](../../javascript/reference/date-object-javascript.md)  
  
## Siehe auch  
 [JSON\-Objekt](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse\-Funktion](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify\-Funktion](../../javascript/reference/json-stringify-function-javascript.md)   
 [JavaScript\-Methoden](../../javascript/reference/javascript-methods.md)
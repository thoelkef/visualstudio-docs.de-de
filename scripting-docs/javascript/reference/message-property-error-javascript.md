---
title: "message-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs"
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
  - "message"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Message-Eigenschaft"
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# message-Eigenschaft (Fehler) (JavaScript)
Gibt eine Zeichenfolge mit einer Fehlermeldung zurück.  
  
## Syntax  
  
```  
  
errorObj.message  
```  
  
## Parameter  
 `errorObj`  
 Erforderlich.  Instanz eines `Error`\-Objekts.  
  
## Hinweise  
 Die `message`\-Eigenschaft gibt die Zeichenfolge mit der Fehlermeldung zurück, die einem bestimmten Fehler zugeordnet ist.  
  
 Dieselben Funktionen werden von der `description`\-Eigenschaft und `message`\-Eigenschaft zur Verfügung gestellt.  Die `description`\-Eigenschaft stellt Abwärtskompatibilität bereit; die `message`\-Eigenschaft ist mit dem ECMA\-Standards konform.  
  
## Beispiel  
 Im folgenden Beispiel werden eine TypeError\-Ausnahme ausgelöst und der Name des Fehlers und die zugehörige Meldung angezeigt.  
  
```javascript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## Beispiel  
 Dieser Code generiert die folgende Ausgabe.  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Gilt für**: [Error\-Objekt](../../javascript/reference/error-object-javascript.md)  
  
## Siehe auch  
 [description\-Eigenschaft \(Fehler\)](../../javascript/reference/description-property-error-javascript.md)   
 [name\-Eigenschaft \(Fehler\)](../../javascript/reference/name-property-error-javascript.md)
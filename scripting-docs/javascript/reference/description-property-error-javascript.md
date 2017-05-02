---
title: "description-Eigenschaft (Eigenschaft) (JavaScript) | Microsoft Docs"
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
  - "Description"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Description-Eigenschaft"
  - "Fehlerbehandlung, Fehlerbeschreibung"
  - "Fehler, Beschreibung"
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# description-Eigenschaft (Eigenschaft) (JavaScript)
Gibt die beschreibende Zeichenfolge, die einem bestimmten Fehler zugeordnet ist, zurück oder legt diese fest.  
  
## Syntax  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## Parameter  
 *object*  
 Erforderlich.  Eine beliebige Instanz eines `Error`\-Objekts.  
  
 `stringExpression`  
 Optional.  Ein Zeichenfolgenausdruck, der eine Beschreibung des Fehlers enthält.  
  
## Hinweise  
 Die **description**\-Eigenschaft enthält die Zeichenfolge der Fehlermeldung, die einem bestimmten Fehler zugeordnet ist.  Verwenden Sie den Wert, der in dieser Eigenschaft enthalten ist, um einen Benutzer vor einem Fehler zu warnen.  
  
 Die **description**\-Eigenschaft und die **message**\-Eigenschaft stellen dieselbe Funktionalität bereit. Die **description**\-Eigenschaft ermöglicht Abwärtskompatibilität, während die **message**\-Eigenschaft dem ECMA\-Standard entspricht.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **description**\-Eigenschaft:  
  
```javascript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Gilt für**: [Error\-Objekt](../../javascript/reference/error-object-javascript.md)  
  
## Siehe auch  
 [number\-Eigenschaft \(Fehler\)](../../javascript/reference/number-property-error-javascript.md)   
 [message\-Eigenschaft \(Fehler\)](../../javascript/reference/message-property-error-javascript.md)   
 [name\-Eigenschaft \(Fehler\)](../../javascript/reference/name-property-error-javascript.md)
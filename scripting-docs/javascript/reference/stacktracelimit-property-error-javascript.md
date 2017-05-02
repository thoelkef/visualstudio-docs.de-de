---
title: "stackTraceLimit-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs"
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
  - "Error.stackTraceLimit"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Fehlerstapellimit [JavaScript]"
  - "JavaScript-Fehlerstapel"
  - "Fehlerstapel [JavaScript]"
  - "JavaScript-Stapelüberwachungslimit"
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# stackTraceLimit-Eigenschaft (Fehler) (JavaScript)
Ruft die Stapelüberwachungsgrenze ab, die der Anzahl der anzuzeigenden Fehlerrahmen entspricht, oder legt sie fest.  Die Standardgrenze ist 10.  
  
## Syntax  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## Hinweise  
 Sie können die `stackTraceLimit`\-Eigenschaft auf einen positiven Wert zwischen 0 und `Infinity` festlegen.  Wenn die Eigenschaft zum Zeitpunkt des Fehlers auf 0 `stackTraceLimit` festgelegt ist, wird keine Stapelüberwachung angezeigt.  Wenn die Eigenschaft auf einen negativen Wert oder einen nicht numerischen Wert festgelegt ist, wird der Wert in 0 konvertiert.  Wenn stackTraceLimit auf `Infinity` festgelegt ist, wird der gesamte Stapel angezeigt.  Andernfalls wird `ToUint32` verwendet, um den Wert zu konvertieren.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie die Stapelüberwachungsgrenze festgelegt und anschließend abgerufen wird.  
  
```javascript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## Anforderungen  
 Wird in Internet Explorer 10 und in der [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-App unterstützt.  
  
 **Gilt für**: [Error\-Objekt](../../javascript/reference/error-object-javascript.md)  
  
## Siehe auch  
 [description\-Eigenschaft \(Fehler\)](../../javascript/reference/description-property-error-javascript.md)   
 [message\-Eigenschaft \(Fehler\)](../../javascript/reference/message-property-error-javascript.md)   
 [name\-Eigenschaft \(Fehler\)](../../javascript/reference/name-property-error-javascript.md)   
 [stack\-Eigenschaft \(Fehler\)](../../javascript/reference/stack-property-error-javascript.md)
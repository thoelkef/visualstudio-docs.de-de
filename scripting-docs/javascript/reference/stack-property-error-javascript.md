---
title: "stack-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs"
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
  - "Error.stack"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Fehlerstapel [JavaScript]"
  - "JavaScript-Fehlerstapel"
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# stack-Eigenschaft (Fehler) (JavaScript)
Ruft den Fehlerstapel als Zeichenfolge ab oder legt ihn fest, der die Stapelüberwachungsrahmen enthält.  
  
## Syntax  
  
```  
  
object  
.stack   
```  
  
## Hinweise  
 Die `stack` \-Eigenschaft wird auf `undefined` festgelegt, wenn der Fehler generiert wird, und er ruft die Ablaufverfolgungsinformationen ab, wenn der Fehler ausgelöst wird.  Wenn ein Fehler mehrere Male ausgelöst wird, wird die `stack`Eigenschaft bei jedem Auslösen des Fehlers aktualisiert.  
  
 Stapelrahmen werden im folgenden Format angezeigt: am Funktionsname \(\< voll qualifizierter Name\/URL\>:\<Zeilennummer\>:\<Spaltennummer\>\)  
  
 Wenn Sie Ihr eigenes Fehlerobjekt erstellen und die Stapelüberwachung auf einen Wert festlegen, wird der Wert beim Auslösen des Fehlers nicht überschrieben.  
  
 Die `stack`\-Eigenschaft zeigt im Rahmen keine Inlinefunktionen an   Es zeigt nur den physischen Stapel an.  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie Sie den Stapel abrufen können, wenn Sie einen Fehler feststellen.  
  
```javascript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie Sie den Stapel festlegen und anschließend abrufen können.  
  
```javascript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]  
  
 **Gilt für**: [Error\-Objekt](../../javascript/reference/error-object-javascript.md)  
  
## Siehe auch  
 [description\-Eigenschaft \(Fehler\)](../../javascript/reference/description-property-error-javascript.md)   
 [message\-Eigenschaft \(Fehler\)](../../javascript/reference/message-property-error-javascript.md)   
 [name\-Eigenschaft \(Fehler\)](../../javascript/reference/name-property-error-javascript.md)   
 [stackTraceLimit\-Eigenschaft \(Fehler\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)
---
title: "String.raw-Funktion (JavaScript) | Microsoft Docs"
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
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# String.raw-Funktion (JavaScript)
Gibt eine Vorlagenzeichenfolge in Form einer unformatierten Zeichenfolge zurück.  
  
## Syntax  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### Parameter  
 `templateStr`  
 Erforderlich.  Die Vorlagenzeichenfolge.  
  
 `obj`  
 Erforderlich.  Ein wohlgeformtes mit der Objektliteralnotation angegebenes Objekt, wie z. B. {raw: 'Wert'}.  
  
 `...substitutions`  
 Dies ist optional.  Ein Array \(ein [Rest\-Parameter](../../javascript/functions-javascript.md)\), das aus einem oder mehreren Ersetzungswerten besteht.  
  
## Hinweise  
 Die `String.raw`\-Funktion ist für die Verwendung mit [Vorlagenzeichenfolgen](../../javascript/advanced/template-strings-javascript.md) vorgesehen.  Die unformatierte Zeichenfolge enthält alle Escapezeichen und umgekehrten Schrägstriche, die in der Zeichenfolge vorhanden sind.  
  
 Ein Fehler wird ausgelöst, wenn `obj` kein wohlgeformtes Objekt ist.  
  
## Beispiel  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
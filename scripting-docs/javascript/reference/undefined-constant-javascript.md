---
title: "nicht definierte Konstante (JavaScript) | Microsoft Docs"
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
  - "undefined"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "undefined-Eigenschaft"
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# nicht definierte Konstante (JavaScript)
Ein Wert, der noch nicht definiert wurde, wie eine Variable, die nicht initialisiert wurde.  
  
## Syntax  
  
```  
undefined  
```  
  
## Hinweise  
 Die Konstante `undefined` ist ein Member des `Global`\-Objekts. Sie ist nach der Initialisierung des Skriptmoduls verfügbar.  Eine Variable, die deklariert, jedoch nicht initialisiert wurde, hat den Wert **undefined**.  
  
 Eine Variable, die nicht deklariert wurde, kann nicht mit `undefined` verglichen werden. Der Typ der Variable kann jedoch mit der Zeichenfolge "undefined" verglichen werden.  
  
 Die `undefined`\-Konstante ist hilfreich, wenn eine Variable ausdrücklich getestet oder auf "undefined" festgelegt werden soll.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `undefined`\-Konstante gezeigt.  
  
```javascript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## Anforderungen  
 Die `undefined`\-Eigenschaft wurde in [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)] eingeführt und in [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)] mit einem Schreibschutz versehen.  
  
 **Gilt für**: [Global\-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## Siehe auch  
 [typeof\-Operator](../../javascript/reference/typeof-operator-decrementjavascript.md)
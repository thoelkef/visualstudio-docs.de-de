---
title: "isPrototypeOf-Methode (Objekt) (JavaScript) | Microsoft Docs"
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
  - "isPrototypeOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isPrototypeOf-Methode"
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# isPrototypeOf-Methode (Objekt) (JavaScript)
Bestimmt, ob ein Objekt in der Prototypenkette eines anderen Objekts vorhanden ist.  
  
## Syntax  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## Parameter  
 `prototype`  
 Erforderlich.  Ein Objektprototyp.  
  
 `object`  
 Erforderlich.  Ein weiteres Objekt, dessen Prototypenkette überprüft werden soll.  
  
## Hinweise  
 Die `isPrototypeOf`\-Methode gibt `true` zurück, wenn `object` in seiner Prototypenkette `prototype` aufweist.  Die Prototypenkette wird verwendet, um die gemeinsame Nutzung von Funktionen zwischen Instanzen desselben Objekttyps zu ermöglichen.  Die `isPrototypeOf`\-Methode gibt `false` zurück, wenn `object` kein Objekt ist oder wenn das `prototype` nicht in der Prototypenkette von `object` enthalten ist.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `isPrototypeOf`\-Methode veranschaulicht.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [prototype\-Eigenschaft \(Objekt\)](../../javascript/reference/prototype-property-object-javascript.md)
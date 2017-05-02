---
title: "Object.setPrototypeOf-Funktion (JavaScript) | Microsoft Docs"
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
ms.assetid: a2609f6e-aeee-4c13-b7cf-c31ddf58ff35
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Object.setPrototypeOf-Funktion (JavaScript)
Legt den Prototyp eines Objekts fest.  
  
## Syntax  
  
```  
Object.setPrototypeOf(obj, proto);  
```  
  
#### Parameter  
 `obj`  
 Erforderlich.  Das Objekt, für das Sie den Prototyp festlegen.  
  
 `proto`  
 Erforderlich.  Der neue Prototyp des Objekts.  
  
## Hinweise  
  
> [!WARNING]
>  Durch das Festlegen des Prototyps kann die Leistung des gesamten JavaScript\-Codes reduziert werden, der Zugriff auf das Objekt hat, dessen Prototyp geändert wurde.  
  
## Beispiel  
 Das folgende Codebeispiel veranschaulicht, wie der Prototyp für ein Objekt festgelegt wird.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns true  
    Object.getPrototypeOf(rec, Object.prototype);  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns false  
}  
```  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie Eigenschaften einem Objekt hinzugefügt werden, indem sie dem Prototypen hinzugefügt werden.  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
Object.getPrototypeOf(obj, proto);  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## Beispiel  
 Im folgenden Codebeispiel werden dem `String`\-Objekt Eigenschaften hinzugefügt, indem ein neuer Prototyp dafür festgelegt wird.  
  
```javascript  
var stringProp = { desc: "description" };  
  
Object.getPrototypeOf(String, stringProp);  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    Object.getPrototypeOf(s1, String); // Can't be set.  
    Object.getPrototypeOf(s2, String);  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
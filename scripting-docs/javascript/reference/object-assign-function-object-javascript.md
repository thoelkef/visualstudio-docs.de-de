---
title: "Object.assign-Funktion (Objekt) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Object.assign-Funktion (Objekt) (JavaScript)
Kopiert die Werte aus einem oder mehreren Quellobjekten in ein Zielobjekt.  
  
## Syntax  
  
```  
Object.assign(target, ...sources );  
```  
  
#### Parameter  
 `target`  
 Erforderlich.  Ein Objekt, in das aufzählbare Eigenschaften kopiert werden.  
  
 `...sources`  
 Erforderlich.  Ein oder mehrere Objekte, aus denen aufzählbare Eigenschaften kopiert werden.  
  
## Ausnahmen  
 Diese Funktion löst einen `TypeError` aus, wenn ein Zuweisungsfehler auftritt, durch den der Kopiervorgang beendet wird.  Ein `TypeError` wird ausgelöst, wenn eine Zieleigenschaft schreibgeschützt ist.  
  
## Hinweise  
 Diese Funktion gibt das Zielobjekt zurück.  Nur *enumerable own*\-Eigenschaften werden aus dem Quellobjekt in das Zielobjekt kopiert.  Sie können diese Funktion verwenden, um Objekte zusammenzuführen oder zu klonen.  
  
 `null`\- oder `undefined`\-Quellen werden wie leere Objekte behandelt und leisten keinen Beitrag zum Zielobjekt.  
  
## Beispiel  
 Im folgenden Codebeispiel wird die Zusammenführung eines Objekts mit `Object.assign` veranschaulicht.  
  
```javascript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## Beispiel  
 Im folgenden Beispiel wird das Klonen eines Objekts mit `Object.assign` veranschaulicht.  
  
```javascript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
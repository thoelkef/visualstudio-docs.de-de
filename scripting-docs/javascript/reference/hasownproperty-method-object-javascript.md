---
title: "hasOwnProperty-Methode (Objekt) (JavaScript) | Microsoft Docs"
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
  - "hasOwnProperty"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "hasOwnProperty-Methode"
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# hasOwnProperty-Methode (Objekt) (JavaScript)
Ermittelt, ob ein Objekt über eine Eigenschaft mit dem angegebenen Namen verfügt.  
  
## Syntax  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## Parameter  
 `object`  
 Erforderlich.  Instanz eines Objekts.  
  
 `proName`  
 Erforderlich.  Zeichenfolgenwert eines Eigenschaftennamens.  
  
## Hinweise  
 Die `hasOwnProperty`\-Methode gibt `true` zurück, wenn `object` über eine Eigenschaft des angegebenen Namens verfügt, andernfalls `false`.  Diese Methode überprüft nicht die Eigenschaften in der Prototypenkette des Objekts; die Eigenschaft muss ein Member des Objekts selbst sein.  
  
 Diese Eigenschaft wird von Hostobjekten für Internet Explorer 8 und ältere Versionen nicht unterstützt.  
  
## Beispiel  
 Im folgenden Beispiel nutzen alle `String`\-Objekte eine gemeinsame split\-Methode.  Der folgenden Code zeigt **false** und **true** an.  
  
```javascript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Siehe auch  
 [in\-Operator](../../javascript/reference/in-operator-decrementjavascript.md)
---
title: "this-Anweisung (JavaScript) | Microsoft Docs"
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
  - "this_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Konstruktoren, Verweisen auf das aktuelle Objekt"
  - "this-Anweisung"
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# this-Anweisung (JavaScript)
Verweist auf das aktuelle Objekt.  
  
## Syntax  
  
```  
this.property  
```  
  
## Hinweise  
 Das erforderliche `property`\-Argument ist eine der Eigenschaften des aktuellen Objekts  
  
 Das `this`\-Schlüsselwort kann in den Objektkonstruktoren verwendet werden, um auf das aktuelle Objekt zu verweisen.  
  
## Beispiel  
 Im folgenden Beispiel bezieht sich **this** auf das neu erstellte Objekt "Car" und weist drei Eigenschaften Werte zu:  
  
```javascript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 Das **this**\-Schlüsselwort bezeichnet im Allgemeinen das **window**\-Objekt, wenn es außerhalb des Bereichs aller anderen Objekte verwendet wird.  Innerhalb eines Ereignishandlers bezeichnet `this` jedoch das DOM\-Element, das das Ereignis ausgelöst hat.  
  
 Im folgenden Code \(für Internet Explorer 9 und höher\) gibt der Ereignishandler die Zeichenfolgenversion einer Schaltfläche mit der ID "Clicker" aus.  
  
```javascript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [new\-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Verwenden der bind\-Methode](../../javascript/advanced/using-the-bind-method-javascript.md)
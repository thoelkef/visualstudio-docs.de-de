---
title: "length-Eigenschaft (Funktion) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Length-Eigenschaft"
  - "length-Eigenschaft (Function)"
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# length-Eigenschaft (Funktion) (JavaScript)
Ruft die Anzahl von Argumenten ab, die für eine Funktion definiert sind.  
  
## Syntax  
  
```  
  
functionName.length  
```  
  
## Hinweise  
 Der erforderliche *functionName* ist der Name der Funktion.  
  
 Die **length**\-Eigenschaft einer Funktion wird vom Skriptmodul nach der Anzahl von Argumenten in der Definition der Funktion initialisiert, wenn eine Instanz der Funktion erstellt wird.  
  
 Welche Situation eintritt, wenn eine Funktion mit einer vom Wert der **length**\-Eigenschaft abweichenden Anzahl von Argumenten aufgerufen wird, hängt von der Funktion ab.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **length**\-Eigenschaft:  
  
```javascript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Siehe auch  
 [arguments\-Eigenschaft \(Funktion\)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length\-Eigenschaft \(Array\)](../../javascript/reference/length-property-array-javascript.md)   
 [length\-Eigenschaft \(String\)](../../javascript/reference/length-property-string-javascript.md)
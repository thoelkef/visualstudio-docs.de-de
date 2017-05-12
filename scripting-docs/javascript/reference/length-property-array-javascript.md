---
title: "length-Eigenschaft (Array) (JavaScript) | Microsoft Docs"
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
  - "Array-Objekt"
  - "Length-Eigenschaft"
  - "length-Eigenschaft (Array)"
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# length-Eigenschaft (Array) (JavaScript)
Ruft die Länge des Arrays ab oder legt sie fest.  Dies ist eine Zahl, die um eins höher ist als das höchste der in einem Array definierten Elemente.  
  
## Syntax  
  
```  
  
numVar = arrayObj.length   
```  
  
## Parameter  
 `numVar`  
 Erforderlich.  Beliebige Zahl.  
  
 `arrayObj`  
 Erforderlich.  Ein `Array`\-Objekt.  
  
## Hinweise  
 In JavaScript haben Arrays eine geringe Dichte, und die Elemente in einem Array müssen nicht zusammenhängend sein.  Die `length`\-Eigenschaft entspricht nicht unbedingt der Anzahl der Elemente im Array.  In der folgenden Arraydefinition enthält `my_array.length` beispielsweise 7 und nicht 2:  
  
```javascript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 Wenn Sie für die `length`\-Eigenschaft einen kleineren als den vorherigen Wert festlegen, wird das Array abgeschnitten, und alle Elemente mit Arrayindizes, die größer oder gleich dem neuen Wert der `length`\-Eigenschaft sind, gehen verloren.  
  
 Wenn Sie für die length\-Eigenschaft einen größeren als den vorherige Wert festlegen, wird das Array erweitert, und alle neu erstellten Elemente haben den Wert `undefined`.  
  
 Das folgende Beispiel veranschaulicht die Verwendung der `length`\-Eigenschaft.  
  
```javascript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  Ab Internet Explorer 9 \(Standardmodus\) werden in die Initialisierung eines Arrays eingeschlossene nachfolgende Trennzeichen anders behandelt.
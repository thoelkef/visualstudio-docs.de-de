---
title: "input-Eigenschaft ($_) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$_"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "$_-Eigenschaft"
  - "input-Eigenschaft"
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# input-Eigenschaft ($_) (RegExp) (JavaScript)
Gibt die Zeichenfolge zurück, für die eine Suche mit einem regulären Ausdruck durchgeführt wurde.  Schreibgeschützt.  
  
## Syntax  
  
```  
  
RegExp.input  
```  
  
## Hinweise  
 Das mit dieser Eigenschaft verknüpfte Objekt ist immer das globale `RegExp`\-Objekt.  
  
 Der Wert der **input**\-Eigenschaft wird geändert, wenn die gesuchte Zeichenfolge geändert wird.  
  
 Das folgende Beispiel veranschaulicht die Verwendung der **input**\-Eigenschaft:  
  
```javascript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [RegExp\-Objekt](../../javascript/reference/regexp-object-javascript.md)  
  
## Siehe auch  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)
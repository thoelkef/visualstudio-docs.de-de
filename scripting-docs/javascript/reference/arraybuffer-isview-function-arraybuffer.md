---
title: "ArrayBuffer.isView-Funktion (ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ArrayBuffer.isView-Funktion (ArrayBuffer)
Bestimmt, ob ob ein Objekt eine Ansicht des Puffers bereitstellt.  
  
## Syntax  
  
```javascript  
ArrayBuffer.isView(object)  
```  
  
#### Parameter  
 `object`  
 Erforderlich.  Das zu überprüfende Objekt.  
  
## Rückgabewert  
 `true`, wenn eine der folgenden Bedingungen zutrifft:  
  
-   `object` ist ein `DataView`\-Objekt.  
  
-   `object` ist ein typisiertes Array.  
  
 Andernfalls gibt diese Methode `false` zurück.  
  
## Hinweise  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `isView`\-Funktion zum Testen eines typisierten Arrays und eines `DataView`\-Objekts.  
  
```javascript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Siehe auch  
 [Uint8ClampedArray\-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)
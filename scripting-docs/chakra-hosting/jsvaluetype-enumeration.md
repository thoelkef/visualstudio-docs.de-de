---
title: "JsValueType-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueType"
helpviewer_keywords: 
  - "JsValueType-Enumeration"
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# JsValueType-Enumeration
Der JavaScript\-Typ von JsValueRef.  
  
## Syntax  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## Mitglieder  
  
### Werte  
  
|Name|Beschreibung|  
|----------|------------------|  
|`JsUndefined`|Der Wert ist der `undefined`\-Wert.|  
|`JsNull`|Der Wert ist der `null`\-Wert.|  
|`JsNumber`|Der Wert ist ein JavaScript\-Zahlenwert.|  
|`JsString`|Der Wert ist ein JavaScript\-Zeichenfolgenwert.|  
|`JsBoolean`|Der Wert ist ein boolescher JavaScript\-Wert.|  
|`JsObject`|Der Wert ist ein JavaScript\-Objektwert.|  
|`JsFunction`|Der Wert ist ein JavaScript\-Funktionsobjektwert.|  
|`JsError`|Der Wert ist ein JavaScript\-Fehlerobjektwert.|  
|`JsArray`|Der Wert ist ein JavaScript\-Arrayobjektwert.|  
|`JsSymbol`|Der Wert ist ein JavaScript\-Symbolwert.<br /><br /> Dieser Enumerationswert wird nur im Edge\-Modus unterstützt.|  
|`JsArrayBuffer`|Der Wert ist ein JavaScript`ArrayBuffer`\-Objektwert.<br /><br /> Dieser Enumerationswert wird nur im Edge\-Modus unterstützt.|  
|`JsTypedArray`|Der Wert ist ein JavaScript\-Typarray\-Objektwert.<br /><br /> Dieser Enumerationswert wird nur im Edge\-Modus unterstützt.|  
|`JsDataView`|Der Wert ist ein JavaScript`DataView`\-Objektwert.<br /><br /> Dieser Enumerationswert wird nur im Edge\-Modus unterstützt.|  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)
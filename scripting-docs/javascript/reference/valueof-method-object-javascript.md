---
title: "valueOf-Methode (Objekt) (JavaScript) | Microsoft Docs"
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
  - "valueOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valueOf-Methode"
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# valueOf-Methode (Objekt) (JavaScript)
Gibt den einfachen Wert des angegebenen Objekts zurück.  
  
## Syntax  
  
```  
  
object.valueOf( )  
```  
  
## Hinweise  
 Der erforderliche `object`\-Verweis ist ein beliebiges systeminternes [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekt.  
  
 Die `valueOf`\-Methode wird für jedes systeminterne [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekt unterschiedlich definiert.  
  
|Objekt|Rückgabewert|  
|------------|------------------|  
|Array|Gibt die Arrayinstanz zurück.|  
|Boolesch|Der Boolesche Wert.|  
|Datum|Der gespeicherte Zeitwert seit dem 1. Januar 1970 UTC um 0:00 Uhr in Millisekunden.|  
|Funktion|Die Funktion selbst.|  
|Nummer|Der numerische Wert.|  
|Objekt|Das Objekt selbst.  Dies ist die Standardeinstellung.|  
|Zeichenfolge|Der Zeichenfolgenwert.|  
  
 Die Objekte **Math** und `Error` haben keine `valueOf`\-Methode.  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]  
  
 **Gilt für**: [Array\-Objekt](../../javascript/reference/array-object-javascript.md)&#124; [Boolean\-Objekt](../../javascript/reference/boolean-object-javascript.md)&#124; [Date\-Objekt](../../javascript/reference/date-object-javascript.md)&#124; [Function\-Objekt](../../javascript/reference/function-object-javascript.md)&#124; [Number\-Objekt](../../javascript/reference/number-object-javascript.md)&#124; [Object\-Objekt](../../javascript/reference/object-object-javascript.md)&#124; [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [toString\-Methode \(Objekt\)](../../javascript/reference/tostring-method-object-javascript.md)
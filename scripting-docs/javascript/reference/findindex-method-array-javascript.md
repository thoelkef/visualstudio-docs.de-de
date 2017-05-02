---
title: "findIndex-Methode (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# findIndex-Methode (Array) (JavaScript)
Gibt einen Indexwert für das erste Arrayelement zurück, das die in einer Rückruffunktion angegebenen Testkriterien erfüllt.  
  
## Syntax  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### Parameter  
 `arrayObj`  
 Erforderlich.  Das Arrayobjekt.  
  
 `callbackfn`  
 Erforderlich.  Die Rückruffunktion zum Testen jedes Elements im Array.  
  
 `thisArg`  
 Optional.  Gibt das `this`\-Objekt in der Rückruffunktion an.  Wenn nicht angegeben, ist das `this`\-Objekt nicht definiert.  
  
## Hinweise  
 Die `findIndex`\-Methode ruft die Rückruffunktion in aufsteigender Reihenfolge einmal für jedes Element im Array auf, bis ein Element `true` wiedergibt.  Sobald ein Element „true“ zurückgibt, gibt `findIndex` den Indexwert des Elements zurück, das „true“ zurückgibt.  Wenn keine Elemente im Array „true“ zurückgeben, gibt `findIndex` \-1 zurück.  
  
 `findIndex` verändert das Arrayobjekt nicht.  
  
## Syntax der Rückruffunktion  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(value, index, thisArg)`  
  
 Beim Deklarieren der Rückruffunktion können bis zu drei Parameter verwendet werden.  
  
 Die Rückruffunktionsparameter lauten wie folgt:  
  
|Rückrufargument|Definition|  
|---------------------|----------------|  
|`value`|Der Wert des Arrayelements.|  
|`index`|Der numerische Index des Arrayelements.|  
|`arrayObj`|Das zu durchsuchende Arrayobjekt.|  
  
## Beispiel  
 Im folgenden Beispiel testet die Rückruffunktion, ob jedes Element im Array gleich 2 ist.  
  
```javascript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## Beispiel  
 Im folgenden Beispiel wird die Pfeilsyntax zum Testen der einzelnen Elemente verwendet.  In diesem Beispiel gibt kein Element `true` zurück, und `findIndex` gibt \-1 zurück.  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../includes/jsv12-md.md)]
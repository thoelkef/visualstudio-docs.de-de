---
title: WeakMap-Objekt (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- WeakMap
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de97f8acb94921090696e9019a1df5d945db7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641740"
---
# <a name="weakmap-object-javascript"></a>WeakMap-Objekt (JavaScript)
Eine Auflistung von Schlüssel/Wert-Paaren, wobei jeder Schlüssel ein Objektverweis ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
weakmapObj = new WeakMap()  
```  
  
## <a name="remarks"></a>Hinweise  
 Ein `WeakMap`-Objekt kann nicht aufgelistet werden.  
  
 Wenn Sie einen Wert mithilfe eines vorhandenen Schlüssels zur Auflistung hinzufügen, ersetzt der neue Wert den alten Wert.  
  
 In einem `WeakMap` Objekt Verweise auf die Schlüsselobjekte werden "schwach" aufrechterhalten. Dies bedeutet, dass `WeakMap` die Ausführung einer Garbage Collection für die Schlüsselobjekte nicht verhindert. Wenn (außer `WeakMap`) keine Verweise auf die Schlüsselobjekten vorhanden sind, kann der Garbage Collector die Schlüsselobjekte erfassen.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `WeakMap`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[Konstruktor](../../javascript/reference/constructor-property-weakmap.md)|Gibt die Funktion an, durch die `WeakMap` erstellt wird.|  
|[Prototyp](../../javascript/reference/prototype-property-weakmap.md)|Gibt einen Verweis auf den Prototyp für `WeakMap` zurück.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `WeakMap`-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Entfernt alle Elemente aus einer `WeakMap`.|  
|[Löschen](../../javascript/reference/delete-method-weakmap-javascript.md)|Entfernt das angegebene Element aus `WeakMap`.|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|Gibt ein angegebenes Element aus `WeakMap` zurück.|  
|[hat](../../javascript/reference/has-method-weakmap-javascript.md)|Gibt `true` zurück, wenn `WeakMap` ein angegebenes Element enthält.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Fügt `WeakMap` ein neues Element hinzu.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Gibt eine Zeichenfolgendarstellung von `WeakMap` zurück.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Gibt den einfachen Wert des angegebenen Objekts zurück.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem `WeakMap`-Objekt Member hinzufügen und sie dann abrufen.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]
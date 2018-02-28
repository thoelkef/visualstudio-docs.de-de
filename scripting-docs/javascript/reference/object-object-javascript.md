---
title: Object-Objekt (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- object
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Object object
ms.assetid: d24ef8fc-217b-4828-94e1-19f72780bae0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17e82b9c66c286c7f847e7b67b1b5928aadd613e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="object-object-javascript"></a>Object-Objekt (JavaScript)
Stellt Funktionen bereit, die allen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Objekten gemeinsam sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
obj  
 = new Object([value])   
```  
  
## <a name="parameters"></a>Parameter  
 `obj`  
 Erforderlich. Der Variablenname, dem das `Object`-Objekt zugewiesen wird.  
  
 *value*  
 Dies ist optional. Ein beliebiger der primitiven [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Datentypen (Zahl, Boolescher Wert oder String). Wenn der Wert ein Objekt ist, wird das Objekt ungeändert zurückgegeben. Wenn *Wert* ist `null`, **undefined**, oder nicht angegeben wird, wird ein Objekt ohne Inhalt erstellt wird.  
  
## <a name="remarks"></a>Hinweise  
 Das `Object`-Objekt ist in allen anderen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Objekten enthalten; alle seine Methoden und Eigenschaften sind in allen anderen Objekten verfügbar. Die Methoden können in benutzerdefinierten Objekten neu definiert werden und werden von [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] zu den entsprechenden Zeitpunkten aufgerufen. Die **ToString** -Methode ist ein Beispiel einer häufig neu definierten `Object` Methode.  
  
 In dieser Sprachreferenz enthält die Beschreibung jeder `Object`-Methode sowohl standardmäßige als auch objektspezifische Implementierungsinformationen für die systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Objekte.  
  
## <a name="requirements"></a>Anforderungen  
 Das `Object Object` wurde in [!INCLUDE[jsv3text](../../javascript/reference/includes/jsv3text-md.md)] eingeführt. Einige Member der folgenden Listen wurden in höheren Versionen eingeführt.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle sind die Eigenschaften des `Object Object`s aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[__proto\_ \_ Eigenschaft](../../javascript/reference/proto-property-object-javascript.md)|Gibt den Prototyp für ein Objekt an.|  
|[constructor-Eigenschaft](../../javascript/reference/constructor-property-object-javascript.md)|Gibt die Funktion an, durch die ein Objekt erstellt wird.|  
|[prototype-Eigenschaft](../../javascript/reference/prototype-property-object-javascript.md)|Gibt einen Verweis auf den Prototyp einer Objektklasse zurück.|  
  
## <a name="functions"></a>Funktionen  
 In der folgenden Tabelle sind die Funktionen des `Object Object`s aufgelistet.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|[Object.Assign-Funktion](../../javascript/reference/object-assign-function-object-javascript.md)|Kopiert die Werte aus einem oder mehreren Quellobjekten in ein Zielobjekt.|  
|[Object.create-Funktion](../../javascript/reference/object-create-function-javascript.md)|Erstellt ein Objekt, das den angegebenen Prototyp besitzt und das optional die angegebenen Eigenschaften enthält.|  
|[Object.defineProperties-Funktion](../../javascript/reference/object-defineproperties-function-javascript.md)|Fügt eine oder mehrere Eigenschaften zu einem Objekt hinzu und/oder ändert Attribute vorhandener Eigenschaften.|  
|[Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md)|Fügt eine Eigenschaft einem Objekt hinzu oder ändert Attribute einer vorhandenen Eigenschaft.|  
|[Object.freeze-Funktion](../../javascript/reference/object-freeze-function-javascript.md)|Verhindert die Änderung von vorhandenen Eigenschaftenattributen und -werten und verhindert die Einführung von neuen Eigenschaften.|  
|[Object.getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|Gibt die Definition einer Dateneigenschaft oder der Zugriffsmethodeneigenschaft zurück.|  
|[Object.getOwnPropertyNames-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md)|Gibt die Namen der Eigenschaften und Methoden eines Objekts zurück.|  
|[Object.getOwnPropertySymbols-Funktion](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)|Gibt die Symboleigenschaften eines Objekts zurück.|  
|[Object.getPrototypeOf-Funktion](../../javascript/reference/object-getprototypeof-function-javascript.md)|Gibt den Prototyp eines Objekts zurück.|  
|[Object.is-Funktion](../../javascript/reference/object-is-function-javascript.md)|Gibt einen Wert zurück, der angibt, ob zwei Werte den gleichen Wert besitzen.|  
|[Object.isExtensible-Funktion](../../javascript/reference/object-isextensible-function-javascript.md)|Gibt einen Wert zurück, der angibt, ob neue Eigenschaften einem Objekt hinzugefügt werden können.|  
|[Object.isFrozen-Funktion](../../javascript/reference/object-isfrozen-function-javascript.md)|Gibt `true` zurück, wenn vorhandene Eigenschaftenattribute und deren Werte in einem Objekt nicht geändert werden können und neue Eigenschaften nicht dem Objekt hinzugefügt werden können.|  
|[Object.isSealed-Funktion](../../javascript/reference/object-issealed-function-javascript.md)|Gibt `true` zurück, wenn vorhandene Eigenschaftenattribute in einem Objekt nicht geändert werden können und neue Eigenschaften nicht dem Objekt hinzugefügt werden können.|  
|[Object.keys-Funktion](../../javascript/reference/object-keys-function-javascript.md)|Gibt die Namen der aufzählbaren Eigenschaften und Methoden eines Objekts zurück.|  
|[Object.preventExtensions-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md)|Verhindert das Hinzufügen neuer Eigenschaften zu einem Objekt.|  
|[Object.seal-Funktion](../../javascript/reference/object-seal-function-javascript.md)|Verhindert die Änderung von Attributen vorhandener Eigenschaften und verhindert die Hinzufügung neuer Eigenschaften.|  
|[Object.setPrototypeOf-Funktion](../../javascript/reference/object-setprototypeof-function-javascript.md)|Legt den Prototyp eines Objekts fest.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle sind die Methoden des `Object Object`s aufgelistet.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[HasOwnProperty-Methode](../../javascript/reference/hasownproperty-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt über eine Eigenschaft mit dem angegebenen Namen verfügt.|  
|[IsPrototypeOf-Methode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt in der Prototypenhierarchie eines anderen Objekts vorhanden ist.|  
|[PropertyIsEnumerable-Methode](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob eine angegebene Eigenschaft Teil eines Objekts ist, und ob sie aufzählbar ist.|  
|[ToLocaleString-Methode](../../javascript/reference/tolocalestring-method-object-javascript.md)|Gibt ein Objekt zurück, das anhand des aktuellen Gebietsschemas in eine Zeichenfolge konvertiert wird.|  
|[ToString-Methode](../../javascript/reference/tostring-method-object-javascript.md)|Gibt eine Zeichenfolgendarstellung eines Objekts zurück.|  
|[ValueOf-Methode](../../javascript/reference/valueof-method-object-javascript.md)|Gibt den einfachen Wert des angegebenen Objekts zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-Objekte](../../javascript/reference/javascript-objects.md)
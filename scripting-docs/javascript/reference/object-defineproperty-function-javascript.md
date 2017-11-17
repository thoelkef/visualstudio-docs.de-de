---
title: Object.defineProperty-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- defineProperty function [JavaScript]
- Object.defineProperty function [JavaScript]
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: "74"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89291f5c836f74a5dd71099328ce389a12f6fd24
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperty-function-javascript"></a>Object.defineProperty-Funktion (JavaScript)
Fügt eine Eigenschaft einem Objekt hinzu oder ändert Attribute einer vorhandenen Eigenschaft.  
  
## <a name="syntax"></a>Syntax  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Das Objekt, zu dem die Eigenschaft hinzugefügt oder dessen Eigenschaft geändert werden soll. Dies kann ein systemeigenes [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Objekt (d. h., ein benutzerdefiniertes Objekt oder ein integriertes Objekt) oder ein DOM-Objekt sein.  
  
 `propertyname`  
 Erforderlich. Eine Zeichenfolge, die den Namen der Eigenschaft enthält.  
  
 `descriptor`  
 Erforderlich. Ein Deskriptor für die Eigenschaft. Er kann sich auf eine Dateneigenschaft oder eine Zugriffsmethodeneigenschaft beziehen.  
  
## <a name="return-value"></a>Rückgabewert  
 Das geänderte Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Sie können die `Object.defineProperty`-Funktion für folgende Aufgaben verwenden:  
  
-   Fügt einem Objekt eine neue Eigenschaft hinzu. Dies geschieht, wenn das Objekt nicht den angegebenen Eigenschaftennamen enthält.  
  
-   Ändert Attribute einer vorhandenen Eigenschaft. Dies geschieht, wenn das Objekt den angegebenen Eigenschaftennamen bereits enthält.  
  
 Die Eigenschaftendefinition wird in einem Deskriptorobjekt bereitgestellt, das die Attribute einer Dateneigenschaft oder einer Accessoreigenschaft beschreibt. Das Deskriptorobjekt ist ein Parameter der `Object.defineProperty`-Funktion.  
  
 Ein Objekt mehrere Eigenschaften hinzufügen oder mehrere vorhandene Eigenschaften zu ändern, können Sie die [Object.defineProperties-Funktion](../../javascript/reference/object-defineproperties-function-javascript.md).  
  
## <a name="exceptions"></a>Ausnahmen  
 Eine `TypeError`-Ausnahme wird ausgelöst, wenn eine der folgenden Bedingungen zutrifft:  
  
-   Das `object`-Argument ist kein Objekt.  
  
-   Das Objekt ist kein [erweiterbare](../../javascript/reference/object-isextensible-function-javascript.md) und der angegebene Eigenschaftenname ist nicht vorhanden...  
  
-   Der `descriptor` verfügt über ein `value`- oder `writable`-Attribut und über ein `get`- oder `set`-Attribut.  
  
-   Der `descriptor` verfügt über ein `get`- oder `set`-Attribut, das keine Funktion ist oder nicht definiert ist.  
  
-   Der angegebene Eigenschaftenname ist bereits vorhanden, die vorhandene Eigenschaft hat ein `configurable`-Attribut mit dem Wert `false`, und der `descriptor` enthält mindestens ein Attribut, das nicht mit den Attributen in der vorhandenen Eigenschaft übereinstimmt. Wenn die vorhandene Eigenschaft jedoch ein `configurable`-Attribut mit dem Wert `false` und ein `writable`-Attribut mit dem Wert `true` enthält, dürfen das `value`- oder `writable`-Attribut unterschiedlich sein.  
  
## <a name="adding-a-data-property"></a>Hinzufügen einer Dateneigenschaft  
 Im folgenden Beispiel fügt die `Object.defineProperty`-Funktion einem benutzerdefinierten Objekt eine Dateneigenschaft hinzu. Um die Eigenschaft stattdessen einem vorhandenen DOM-Objekt hinzuzufügen, heben Sie die Auskommentierung der `var = window.document`-Zeile auf.  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property to the object.  
Object.defineProperty(obj, "newDataProperty", {  
    value: 101,  
    writable: true,  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newDataProperty = 102;  
document.write("Property value: " + obj.newDataProperty + newLine);  
  
// Output:  
// Property value: 102  
```  
  
 Um die Objekteigenschaften aufzulisten, fügen Sie diesem Beispiel den folgenden Code hinzu.  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## <a name="modifying-a-data-property"></a>Ändern einer Dateneigenschaft  
 Um ein Eigenschaftenattribut für das Objekt zu ändern, fügen Sie der weiter oben dargestellten `addDataProperty`-Funktion den folgenden Code hinzu. Der `descriptor`-Parameter enthält nur ein `writable`-Attribut. Die anderen Dateneigenschaftenattribute bleiben unverändert.  
  
```JavaScript  
// Modify the writable attribute of the property.  
Object.defineProperty(obj, "newDataProperty", { writable: false });  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output  
// writable: false  
// value: 102  
// configurable: true  
// enumerable: true  
```  
  
## <a name="adding-an-accessor-property"></a>Hinzufügen einer Accessor-Eigenschaft  
 Im folgenden Beispiel fügt die `Object.defineProperty`-Funktion einem benutzerdefinierten Objekt eine Accessoreigenschaft hinzu.  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add an accessor property to the object.  
Object.defineProperty(obj, "newAccessorProperty", {  
    set: function (x) {  
        document.write("in property set accessor" + newLine);  
        this.newaccpropvalue = x;  
    },  
    get: function () {  
        document.write("in property get accessor" + newLine);  
        return this.newaccpropvalue;  
    },  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newAccessorProperty = 30;  
document.write("Property value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// Property value: 30  
  
```  
  
 Um die Objekteigenschaften aufzulisten, fügen Sie diesem Beispiel den folgenden Code hinzu.  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
// Output:  
// in property get accessor  
// newAccessorProperty: 30  
  
```  
  
## <a name="modifying-an-accessor-property"></a>Ändern einer Accessor-Eigenschaft  
 Um ein Eigenschaftenattribut für das Objekt zu ändern, fügen Sie dem weiter oben dargestellten Code den folgenden Code hinzu. Der `descriptor`-Parameter enthält nur eine `get`-Accessordefinition. Die anderen Eigenschaftenattribute bleiben unverändert.  
  
```JavaScript  
// Modify the get accessor.  
Object.defineProperty(obj, "newAccessorProperty", {  
    get: function () { return this.newaccpropvalue; }  
});  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newAccessorProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output:  
// get: function () { return this.newaccpropvalue; }  
// set: function (x) { document.write("in property set accessor" + newLine); this.newaccpropvalue = x; }  
// configurable: true  
// enumerable: true  
```  
  
## <a name="modifying-a-property-on-a-dom-element"></a>Ändern einer Eigenschaft in einem DOM-Element  
 Im folgenden Beispiel wird veranschaulicht, wie integrierte DOM-Eigenschaften angepasst werden, indem mit der `Object.getOwnPropertyDescriptor`-Funktion der Eigenschaftendeskriptor der Eigenschaft abgerufen und geändert wird. Für dieses Beispiel muss ein DIV-Element mit der ID "div" vorhanden sein.  
  
```JavaScript  
// Get the querySelector property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(Element.prototype, "querySelector");  
  
// Make the property read-only.  
descriptor.value = "query";  
descriptor.writable = false;  
// Apply the changes to the Element prototype.  
Object.defineProperty(Element.prototype, "querySelector", descriptor);  
  
// Get a DOM element from the HTML body.  
var elem = document.getElementById("div");  
  
// Attempt to change the value. This causes the revised value attribute to be called.  
elem.querySelector = "anotherQuery";  
document.write(elem.querySelector);  
  
// Output:  
// query  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 Internet Explorer 9 (Standardmodus) und Internet Explorer 10 (Standardmodus) sowie [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]-Apps unterstützen alle Funktionen.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] unterstützt DOM-Objekte, jedoch keine benutzerdefinierten Objekte. Die Attribute `enumerable` und `configurable` können angegeben werden, werden jedoch nicht verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentobjektmodell-Prototypen, Teil 2: Zugriffsmethode (Getter/Setter) unterstützen](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperties-Funktion](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Object.Create-Funktion](../../javascript/reference/object-create-function-javascript.md)   
 [Object.getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md)
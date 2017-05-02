---
title: "Object.defineProperties-Funktion (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "Object.defineProperties-Funktion [JavaScript]"
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Object.defineProperties-Funktion (JavaScript)
Fügt eine oder mehrere Eigenschaften zu einem Objekt hinzu und\/oder ändert Attribute vorhandener Eigenschaften.  
  
## Syntax  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## Parameter  
 `object`  
 Erforderlich.  Das Objekt, zu dem die Eigenschaft hinzugefügt oder dessen Eigenschaften geändert werden sollen.  Dies kann ein systemeigenes [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekt oder ein DOM\-Objekt sein.  
  
 `descriptors`  
 Erforderlich.  Ein [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekt, das eine oder mehrere Deskriptorobjekte enthält.  Jedes Deskriptorobjekt beschreibt eine Dateneigenschaft oder eine Accessoreigenschaft.  
  
## Rückgabewert  
 Das an die Funktion übergebene Objekt.  
  
## Hinweise  
 Das `descriptors`\-Argument ist ein Objekt, das ein oder mehrere Deskriptorobjekte enthält.  
  
 Eine *Dateneigenschaft* ist eine Eigenschaft, die einen Wert speichern und abrufen kann.  Ein Dateneigenschaftendeskriptor enthält ein `value`\-Attribut, ein `writable`\-Attribut oder beides.  Weitere Informationen finden Sie unter [Dateneigenschaften und Accessor\-Eigenschaften](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 Eine *Accessoreigenschaft* ruft eine vom Benutzer bereitgestellte Funktion immer dann auf, wenn der Eigenschaftswert festgelegt oder abgerufen wird.  Ein Accessoreigenschaftendeskriptor enthält ein `set`\-Attribut, ein `get`\-Attribut oder beides.  
  
 Wenn das Objekt bereits eine Eigenschaft mit dem angegebenen Namen besitzt, werden die Eigenschaftenattribute geändert.  Weitere Informationen finden Sie unter [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Um ein Objekt zu erstellen und Eigenschaften zum neuen Objekt hinzuzufügen, können Sie [Object.create\-Funktion](../../javascript/reference/object-create-function-javascript.md) verwenden.  
  
## Hinzufügen von Eigenschaften  
 Im folgenden Beispiel fügt die `Object.defineProperties`\-Funktion eine Dateneigenschaft und eine Accessoreigenschaft zu einem benutzerdefinierten Objekt hinzu.  
  
 Im Beispiel wird ein Objektliteral verwendet, um das `descriptors`\-Objekt mit dem `newDataProperty`\-Deskriptorobjekt und dem `newAccessorProperty`\-Deskriptorobjekt zu erstellen.  
  
```javascript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
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
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 Wie im vorherigen Beispiel werden im folgenden Beispiel Eigenschaften dynamisch anstatt mit Objektliteral hinzugefügt.  
  
```javascript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## Ändern von Eigenschaften  
 Um Eigenschaftenattribute für das Objekt zu ändern, fügen Sie den folgenden Code hinzu.  Die `Object.defineProperties`\-Funktion ändert das `writable`\-Attribut von `newDataProperty` und das `enumerable`\-Attribut von `newAccessorProperty`.  Sie fügt `anotherDataProperty` zum Objekt hinzu, da dieser Eigenschaftsname noch nicht vorhanden ist.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## Anforderungen  
 Wird in Internet Explorer 9 \(Standardmodus\), in Internet Explorer 10 \(Standardmodus\) und in [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-Apps unterstützt.  Unterstützt in Internet Explorer 8 für DOM\-Objekte; andernfalls keine Unterstützung.  
  
## Siehe auch  
 [Object.getOwnPropertyDescriptor\-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames\-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.create\-Funktion](../../javascript/reference/object-create-function-javascript.md)   
 [Object\-Objekt](../../javascript/reference/object-object-javascript.md)
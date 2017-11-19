---
title: Object.defineProperties-Funktion (JavaScript) | Microsoft Docs
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
helpviewer_keywords: Object.defineProperties function [JavaScript]
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f4f5817a105283a26c971bd98869d000ca0bc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperties-function-javascript"></a>Object.defineProperties-Funktion (JavaScript)
Fügt eine oder mehrere Eigenschaften zu einem Objekt hinzu und/oder ändert Attribute vorhandener Eigenschaften.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Das Objekt auf das Hinzufügen oder Ändern der Eigenschaften. Dies kann ein systemeigenes [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekt oder ein DOM-Objekt.  
  
 `descriptors`  
 Erforderlich. Ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekt, das ein oder mehrere Deskriptor Objekte enthält. Jede Deskriptorobjekt beschreibt eine Dateneigenschaft oder einer Accessor-Eigenschaft.  
  
## <a name="return-value"></a>Rückgabewert  
 Das Objekt, das an die Funktion übergeben wurde.  
  
## <a name="remarks"></a>Hinweise  
 Die `descriptors` Argument ist ein Objekt, das ein oder mehrere Deskriptor Objekte enthält.  
  
 Ein *Dateneigenschaft* ist eine Eigenschaft, speichern und einen Wert abrufen kann. Ein dateneigenschaftendeskriptor enthält ein `value` -Attribut, eine `writable` -Attribut oder beides. Weitere Informationen finden Sie unter [Dateneigenschaften und Accessoreigenschaften](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 Ein *Accessoreigenschaft* eine vom Benutzer bereitgestellte Funktion aufruft, jedes Mal, wenn der Eigenschaftswert festgelegt oder abgerufen wird. Ein Accessoreigenschaftendeskriptor enthält ein `set`-Attribut, ein `get`-Attribut oder beides.  
  
 Wenn das Objekt bereits eine Eigenschaft, die den angegebenen Namen verfügt enthält, werden die Eigenschaftenattribute geändert. Weitere Informationen finden Sie unter [Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Erstellen ein Objekt, und Eigenschaften in das neue Objekt hinzufügen, können Sie die [Object.create-Funktion](../../javascript/reference/object-create-function-javascript.md).  
  
## <a name="adding-properties"></a>Hinzufügen von Eigenschaften  
 Im folgenden Beispiel die `Object.defineProperties` Funktion fügt eine Dateneigenschaft und einer Accessor-Eigenschaft mit einem benutzerdefinierten Objekt.  
  
 Im Beispiel wird ein Objektliteral zum Erstellen der `descriptors` -Objekt mit den `newDataProperty` und `newAccessorProperty` Deskriptor-Objekte.  
  
```JavaScript  
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
  
 Wie die oben aufgeführten Beispiel fügt das folgende Beispiel Eigenschaften dynamisch anstelle von mit einem Objektliteral.  
  
```JavaScript  
  
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
  
## <a name="modifying-properties"></a>Ändern von Eigenschaften  
 Um Attribute für das Objekt zu ändern, fügen Sie den folgenden Code ein. Die `Object.defineProperties` Funktion ändert den `writable` Attribut des `newDataProperty`, und ändert die `enumerable` Attribut des `newAccessorProperty`. Es fügt `anotherDataProperty` auf das Objekt, da dieser Eigenschaftenname noch nicht vorhanden ist.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## <a name="requirements"></a>Anforderungen  
 Unterstützt in Internet Explorer 9-Standardmodus, Internet Explorer 10-Standards und [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] apps. Unterstützt in Internet Explorer 8 für DOM-Objekte nur ansonsten nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Object.getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.Create-Funktion](../../javascript/reference/object-create-function-javascript.md)   
 [Object-Objekt](../../javascript/reference/object-object-javascript.md)
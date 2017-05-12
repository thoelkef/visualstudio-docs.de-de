---
title: "Object.getOwnPropertyDescriptor-Funktion (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyDescriptor-Methode [JavaScript]"
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# Object.getOwnPropertyDescriptor-Funktion (JavaScript)
Ruft den eigenen Eigenschaftendeskriptor des angegebenen Objekts ab.  Ein eigener Eigenschaftendeskriptor ist ein Deskriptor, der direkt für das Objekt definiert wird und nicht vom Prototyp des Objekts geerbt wird.  
  
## Syntax  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## Parameter  
 `object`  
 Erforderlich.  Das Objekt, das die Eigenschaft enthält.  
  
 `propertyname`  
 Erforderlich.  Der Name der Eigenschaft.  
  
## Rückgabewert  
 Der Deskriptor der Eigenschaft.  
  
## Hinweise  
 Sie können mit der `Object.getOwnPropertyDescriptor`\-Funktion ein Deskriptorobjekt abrufen, das Attribute der Eigenschaft beschreibt.  
  
 Die [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md) wird verwendet, um Eigenschaften hinzufügen oder zu ändern.  
  
## Beispiel für Dateneigenschaften  
 Im folgenden Beispiel wird ein Dateneigenschaftendeskriptor abgerufen und verwendet, um die Eigenschaft mit einem Schreibschutz zu versehen.  
  
```javascript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 Um die Eigenschaftenattribute aufzulisten, können Sie dem Beispiel den folgenden Code hinzufügen.  
  
```javascript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## Anforderungen  
 Alle Funktionen werden in [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] unterstützt.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] unterstützt DOM\-Objekte, jedoch keine benutzerdefinierten Objekte.  Die Attribute `enumerable` und `configurable` können angegeben werden, werden jedoch nicht verwendet.  
  
## Siehe auch  
 [Dokumentobjektmodell\-Prototypen, Teil 2: Accessorunterstützung \(getter\/setter\)](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md)
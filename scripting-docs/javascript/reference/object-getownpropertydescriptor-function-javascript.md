---
title: Object.getOwnPropertyDescriptor-Funktion (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getOwnPropertyDescriptor method [JavaScript]
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 45
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd147d567fc4d8a39d7a251d55772c40518e7a26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639030"
---
# <a name="objectgetownpropertydescriptor-function-javascript"></a>Object.getOwnPropertyDescriptor-Funktion (JavaScript)
Ruft den eigenen Eigenschaftendeskriptor des angegebenen Objekts ab. Ein eigener Eigenschaftendeskriptor ist ein Deskriptor, der direkt für das Objekt definiert wird und nicht vom Prototyp des Objekts geerbt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Das Objekt, das die Eigenschaft enthält.  
  
 `propertyname`  
 Erforderlich. Den Namen der Eigenschaft.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Deskriptor der Eigenschaft.  
  
## <a name="remarks"></a>Hinweise  
 Sie können mit der `Object.getOwnPropertyDescriptor`-Funktion ein Deskriptorobjekt abrufen, das Attribute der Eigenschaft beschreibt.  
  
 Die [Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md) wird verwendet, um Eigenschaften hinzufügen oder ändern.  
  
## <a name="data-property-example"></a>Beispiel für Dateneigenschaften  
 Im folgenden Beispiel wird ein Dateneigenschaftendeskriptor abgerufen und verwendet, um die Eigenschaft mit einem Schreibschutz zu versehen.  
  
```JavaScript  
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
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 Alle Funktionen werden in [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] unterstützt.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] unterstützt DOM-Objekte, jedoch keine benutzerdefinierten Objekte. Die Attribute `enumerable` und `configurable` können angegeben werden, werden jedoch nicht verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentobjektmodell-Prototypen, Teil 2: Zugriffsmethode (Getter/Setter) unterstützen](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md)
---
title: Prototypen und Prototypvererbung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- prototype [JavaScript]
- prototype inheritance [JavaScript]
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 200ca757e72b2eec8f09fd48a841cc8eb816c85d
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
ms.locfileid: "29899944"
---
# <a name="prototypes-and-prototype-inheritance"></a>Prototypen und Prototypvererbung
In JavaScript ist ein `prototype` eine Eigenschaft von Funktionen und Objekten, die von Konstruktorfunktionen erstellt werden. Der Prototyp einer Funktion ist ein Objekt. Der Hauptverwendungszweck ist, wenn eine Funktion als Konstruktor verwendet wird.  
  
```JavaScript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 Im oben genannten Beispiel ist der Prototyp der `Vehicle`-Funktion der Prototyp aller Objekte, die mit dem `Vehicle`-Konstruktor instanziiert werden.  
  
## <a name="using-prototypes-to-add-properties-and-methods"></a>Verwenden von Prototypen zum Hinzufügen von Eigenschaften und Methoden  
 Sie können die `prototype`-Eigenschaft verwenden, um Eigenschaften und Methoden zu Objekten hinzuzufügen, auch wenn diese bereits erstellt wurden:  
  
```JavaScript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 Der Wert von `testColor` ist "Rot".  
  
 Sie können Eigenschaften und Methoden sogar vordefinierten Objekten hinzufügen. Beispielsweise können Sie eine `Trim`-Methode für das `String`-Prototypobjekt definieren, und alle Zeichenfolgen im Skript erben die Methode.  
  
```JavaScript  
String.prototype.trim = function()  
{  
    // Replace leading and trailing spaces with the empty string  
    return this.replace(/(^\s*)|(\s*$)/g, "");  
}  
var s = "    leading and trailing spaces    ";  
// Displays "    leading and trailing spaces     (35)"  
window.alert(s + " (" + s.length + ")");  
// Remove the leading and trailing spaces  
s = s.trim();  
// Displays "leading and trailing spaces (27)"  
window.alert(s + " (" + s.length + ")");  
```  
  
### <a name="using-prototypes-to-derive-one-object-from-another-with-objectcreate"></a>Verwenden von Prototypen zum Ableiten von Objekten aus anderen mit "Object.create"  

Der `Object`-Prototyp kann verwendet werden, um ein Objekt von einem anderen abzuleiten. Beispielsweise können Sie die [Object.create](../../javascript/reference/object-create-function-javascript.md)-Funktion verwenden, um ein neues `Bicycle`-Objekt mithilfe des Prototyps des zuvor definierten `Vehicle`-Objekts abzuleiten (sowie alle neuen erforderlichen Eigenschaften).  
  
```JavaScript  
var bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 Das `bicycle`-Objekt verfügt über die `wheels`-, `engine`-, `color`- und `pedals`-Eigenschaft, und der Prototyp ist `Vehicle.prototype`. Das JavaScript-Modul durchsucht die `pedals`-Eigenschaft für `bicycle` sowie die Prototypenkette, um nach den `wheels`-, `engine`- und `color`-Eigenschaften für `Vehicle` zu suchen.  
  
### <a name="changing-an-objects-prototype"></a>Ändern des Prototyps eines Objekts  
In Internet Explorer 11 können Sie den internen Prototyp eines Objekts oder einer Funktion durch einen neuen Prototyp ersetzen, indem Sie die Eigenschaft [__proto__](../../javascript/reference/proto-property-object-javascript.md) verwenden. Wenn Sie diese Eigenschaft verwenden, erben Sie die Eigenschaften und Methoden des neuen Prototyps zusammen mit anderen Eigenschaften und Methoden in der Prototypenkette.  

> [!WARNING]
> Die `__proto__`-Eigenschaft ist ein Legacyfeature. Verwenden Sie stattdessen [Object.getPrototypeOf](../reference/object-getprototypeof-function-javascript.md).
  
Das folgende Beispiel zeigt, wie Sie den Prototyp eines Objekts ändern können. Dieses Beispiel zeigt, wie sich die geerbten Eigenschaften des Objekts ändern, wenn Sie dessen Prototyp ändern.  
  
```JavaScript  
function Friend() {  
    this.demeanor = "happy";  
}  
  
function Foe() {  
    this.demeanor = "suspicious";  
}  
  
var friend = new Friend();  
var foe = new Foe();  
  
var player = new Object();  
player.__proto__ = foe;  
  
friend.ally = "Tom";  
  
if (console && console.log) {  
    console.log(player.demeanor === "happy" );      // Returns false  
    console.log(player.demeanor === "suspicious");  // Returns true  
    console.log(player.ally === "Tom");             // Returns false  
    // Turn the foe to a friend.  
    player.__proto__ = friend;  
    console.log(player.demeanor === "happy");       // Returns true  
    console.log(player.demeanor === "suspicious");  // Returns false  
    console.log(player.ally === "Tom");             // Returns true  
}  
```

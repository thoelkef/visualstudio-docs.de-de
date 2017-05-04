---
title: "Prototypen und Prototypvererbung | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Prototyp [JavaScript]"
  - "Prototypvererbung [JavaScript]"
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Prototypen und Prototypvererbung
In JavaScript ist ein `prototype` eine Eigenschaft von Funktionen und Objekten, die von Konstruktorfunktionen erstellt werden.  Der Prototyp einer Funktion ist ein Objekt.  Der Hauptverwendungszweck ist, wenn eine Funktion als Konstruktor verwendet wird.  
  
```javascript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 Im oben genannten Beispiel ist der Prototyp der `Vehicle`\-Funktion der Prototyp aller Objekte, die mit dem `Vehicle`\-Konstruktor instanziiert werden.  
  
## Verwenden von Prototypen zum Hinzufügen von Eigenschaften und Methoden  
 Sie können die `prototype`\-Eigenschaft verwenden, um Eigenschaften und Methoden zu Objekten hinzuzufügen, auch wenn diese bereits erstellt wurden:  
  
```javascript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 Der Wert von `testColor` ist "Rot".  
  
 Sie können Eigenschaften und Methoden sogar vordefinierten Objekten hinzufügen.  Beispielsweise können Sie eine `Trim`\-Methode für das `String`\-Prototypobjekt definieren, und alle Zeichenfolgen im Skript erben die Methode.  
  
```javascript  
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
  
### Verwenden von Prototypen zum Ableiten von Objekten aus anderen mit "Object.create"  
 Das `prototype`\-Objekt kann verwendet werden, um ein Objekt aus einem anderen abzuleiten.  Beispielsweise können Sie die [Object.create](../../javascript/reference/object-create-function-javascript.md)\-Funktion verwenden, um ein neues `Bicycle`\-Objekt mithilfe des Prototyps des zuvor definierten `Vehicle`\-Objekts abzuleiten \(sowie alle neuen erforderlichen Eigenschaften\).  
  
```javascript  
var Bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 Das `Bicycle`\-Objekt verfügt über die `wheels`\-, `engine`\-, `color`\- und `pedals`\-Eigenschaft, und der Prototyp ist `Vehicle.prototype`.  Das JavaScript\-Modul durchsucht die `pedals`\-Eigenschaft für `Bicycle` sowie die Prototypenkette, um nach den `wheels`\-, `engine`\- und `color`\-Eigenschaften für `Vehicle` zu suchen.  
  
### Ändern des Prototyps eines Objekts  
 In Internet Explorer 11, können Sie den internen Prototyp eines Objekts oder einer Funktion durch einen neuen Prototyp ersetzen, indem Sie die Eigenschaft [\_\_proto\_\_](../../javascript/reference/proto-property-object-javascript.md) verwenden.  Wenn Sie diese Eigenschaft verwenden, erben Sie die Eigenschaften und Methoden des neuen Prototyps zusammen mit anderen Eigenschaften und Methoden in der Prototypenkette.  
  
 Das folgende Beispiel zeigt, wie Sie den Prototyp eines Objekts ändern können.  Dieses Beispiel zeigt, wie sich die geerbten Eigenschaften des Objekts ändern, wenn Sie dessen Prototyp ändern.  
  
```javascript  
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
---
title: "Objekte und Arrays (JavaScript) | Microsoft Docs"
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
  - "Arrays [JavaScript]"
  - "Arrays [JavaScript], Objekte"
ms.assetid: f5106284-1240-4f47-8c3b-5a45e227e5e1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Objekte und Arrays (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\-Objekte sind Auflistungen von Eigenschaften und Methoden.  Eine Methode ist eine Funktion, die ein Member eines Objekts ist.  Eine Eigenschaft ist ein Wert oder ein Satz von Werten \(in Form eines Arrays oder eines Objekts\), der Member eines Objekts ist.  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] unterstützt vier Arten von Objekten:  
  
-   Systeminterne Objekte, wie z. B. `Array` und `String`.  
  
-   Objekte, die Sie erstellen.  
  
-   Hostobjekte, wie z. B. `window` und `document`.  
  
-   ActiveX\-Objekte.  
  
## Expando\-Eigenschaften und \-Methoden  
 Alle Objekte in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] unterstützen "expando"\-Eigenschaften\- und Methoden, die zur Laufzeit hinzugefügt und entfernt werden können.  Diese Eigenschaften und Methoden können beliebige Namen haben und von Zahlen identifiziert werden.  Wenn der Name der Eigenschaft oder der Methode ein einfacher Bezeichner ist, kann er mit einem Punkt nach dem Objektnamen geschrieben werden, z. B. wie `myObj.name`, `myObj.age` und `myObj.getAge` im folgenden Code:  
  
```javascript  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.age = 42;  
  
myObj.getAge =   
    function () {  
        return this.age;  
    };  
  
document.write(myObj.name);  
document.write("<br/>");  
document.write(myObj.age);  
document.write("<br/>");  
document.write(myObj.getAge());  
  
// Output:  
// Fred  
// 42  
// 42  
  
```  
  
 Wenn der Name der Eigenschaft oder der Methode kein einfacher Bezeichner ist oder beim Erstellen des Skripts nicht bekannt ist, können Sie einen beliebigen Ausdruck in eckigen Klammern verwenden, um die Eigenschaft zu indizieren.  In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] werden die Namen aller expando\-Eigenschaften in Zeichenfolgen konvertiert, bevor sie zum Objekt hinzugefügt werden.  
  
```javascript  
var myObj = new Object();  
  
// Add two expando properties that cannot be written in the  
// object.property syntax.  
// The first contains invalid characters (spaces), so must be  
// written inside square brackets.  
myObj["not a valid identifier"] = "This is the property value";  
  
// The second expando name is a number, so it also must  
// be placed inside square brackets  
myObj[100] = "100";  
```  
  
 Informationen zum Erstellen eines Objekts anhand einer Definition finden Sie unter [Erstellen von Objekten](../javascript/creating-objects-javascript.md).  
  
## Arrays als Objekte  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] werden Objekte und Arrays fast identisch behandelt, da Arrays lediglich eine spezielle Art von Objekten sind.  Sowohl Objekte als auch Arrays können Eigenschaften und Methoden besitzen.  
  
 Arrays haben eine `length`\-Eigenschaft, Objekte hingegen nicht.  Wenn Sie einem Element eines Arrays einen Wert zuweisen, dessen Index größer als seine Länge \(beispielsweise, `myArray[100] = "hello"`\) ist, wird die `length`\-Eigenschaft automatisch auf die neue Länge erhöht.  Dementsprechend werden alle Elemente, deren Index sich außerhalb der Länge des Arrays befinden, gelöscht, wenn Sie die `length`\-Eigenschaft eines Arrays verringern.  
  
```javascript  
// An array with three elements  
var myArray = new Array(3);  
  
// Add some data  
myArray[0] = "Hello";  
myArray[1] = 42;  
myArray[2] = new Date(2000, 1, 1);  
  
document.write("original length is: " + myArray.length);  
document.write("<br/>");  
// Add some expando properties  
myArray.expando = "JavaScript!";  
myArray["another Expando"] = "Windows";  
  
// This will still display 3, since the two expando properties  
// don't affect the length.  
document.write("new length is : " + myArray.length);  
  
// Output:  
// original length is: 3  
// new length is : 3  
  
```  
  
 Arrays enthalten Methoden, um Member zu durchlaufen und zu bearbeiten.  Das folgende Beispiel zeigt, wie die Eigenschaften von Objekten, die in einem Array gespeichert sind, abgerufen werden.  
  
```javascript  
var myArray = new Array(3);  
  
// Add some data  
for(var i = 1; i <= 3; i++) {  
    myArray[i] = new Date(2000 + i, 1, 1);  
}  
  
myArray.forEach(function (item) {  
    document.write(item.getFullYear());  
});  
  
// Output:  
// 2001  
// 2002  
// 2003  
```  
  
## Mehrdimensionale Arrays  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] unterstützt nicht direkt mehrdimensionale Arrays, aber Sie können das Verhalten von mehrdimensionalen Arrays abrufen, indem Sie Arrays in den Elementen eines anderen Arrays speichern. \(Sie können jede Art von Daten innerhalb der Arrayelemente speichern, einschließlich andere Arrays.\) Mit dem folgenden Code wird z. B. eine Multiplikationstabelle für die Zahlen bis 5 erstellt.  
  
```javascript  
// The size of the table.  
var iMaxNum = 5;  
// Loop counters.  
var i, j;  
  
// Set the length of the array to iMaxNum + 1.   
// The first array index is zero, not 1.  
var MultiplicationTable = new Array(iMaxNum + 1);  
  
// Loop for each major number (each row in the table)  
for (i = 1; i <= iMaxNum; i++)  
{  
    // Create the columns in the table  
    MultiplicationTable[i] = new Array(iMaxNum + 1);  
  
    // Fill the row with the results of the multiplication  
    for (j = 1; j <= iMaxNum; j++)  
    {  
        MultiplicationTable[i][j] = i * j;  
    }  
}  
  
document.write(MultiplicationTable[3][4]);  
document.write("<br/>");   
document.write(MultiplicationTable[5][2]);  
document.write("<br/>");  
document.write(MultiplicationTable[1][4]);  
  
// Output:  
// 12  
// 10  
// 4  
  
```
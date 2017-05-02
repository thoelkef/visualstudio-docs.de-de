---
title: "Systeminterne Objekte (JavaScript) | Microsoft Docs"
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
  - "integrierte Objekte [JavaScript]"
  - "systeminterne Objekte [JavaScript]"
ms.assetid: 6520c634-a7d1-4a05-8c1b-2e79f449d2e4
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Systeminterne Objekte (JavaScript)
[!INCLUDE[javascript](../includes/javascript-md.md)] stellt systeminterne \(oder „integrierte“\) Objekte bereit.  Es handelt sich dabei um die Objekte `Array`, `Boolean`, `Date`, `Error`, `Function`, **Global**, **JSON**, **Math**, **Number**, `Object`, `RegExp` und `String`.  Die systeminternen Objekte verfügen über zugehörige Methoden, Funktionen, Eigenschaften und Konstanten, die in der [Sprachreferenz](../javascript/reference/javascript-reference.md) ausführlich beschrieben werden.  
  
## Array\-Objekt  
 Die Feldindizes eines Arrays können als Eigenschaften eines Objekts betrachtet werden und werden durch ihren numerischen Index bezeichnet.  Beachten Sie, dass die benannten Eigenschaften, die einem Array hinzugefügt werden, nicht durch Zahlen indiziert werden können; sie sind von den Arrayelementen getrennt.  
  
 Um ein neues Array zu erstellen, verwenden Sie den **new**\-Operator und den **Array\(\)**\-[Konstruktor](../javascript/reference/constructor-property-object-javascript.md) wie im folgenden Beispiel.  
  
```javascript  
var theMonths = new Array(12);  
theMonths[0] = "Jan";  
theMonths[1] = "Feb";  
theMonths[2] = "Mar";  
theMonths[3] = "Apr";  
theMonths[4] = "May";  
theMonths[5] = "Jun";  
theMonths[6] = "Jul";  
theMonths[7] = "Aug";  
theMonths[8] = "Sep";  
theMonths[9] = "Oct";  
theMonths[10] = "Nov";  
theMonths[11] = "Dec";  
```  
  
 Wenn Sie unter Verwendung des Schlüsselworts `Array` ein Array erstellen, nimmt [!INCLUDE[javascript](../includes/javascript-md.md)] eine **length**\-Eigenschaft in das Array auf, die die Anzahl der Einträge aufzeichnet.  Wenn Sie keine Zahl angeben, wird die Länge auf 0 gesetzt, und das Array enthält keine Einträge.  Wenn Sie eine Zahl angeben, wird die length\-Eigenschaft auf diesen Wert festgelegt.  Wenn Sie mehr als einen Parameter angeben, werden diese Parameter als Einträge im Array verwendet.  Der length\-Eigenschaft wird zusätzlich die Anzahl der Parameter zugewiesen. Betrachten Sie dazu das folgende Beispiel, das äquivalent zum vorherigen Beispiel ist.  
  
```javascript  
var theMonths = new Array("Jan", "Feb", "Mar", "Apr", "May", "Jun",   
"Jul", "Aug", "Sep", "Oct", "Nov", "Dec");  
```  
  
 [!INCLUDE[javascript](../includes/javascript-md.md)] ändert automatisch den Wert von **length**, wenn Sie Elemente einem Array hinzufügen, das mit dem Schlüsselwort `Array` erstellt wurde.  Arrayindizes beginnen in [!INCLUDE[javascript](../includes/javascript-md.md)] immer bei 0 und nicht bei 1. Daher ist der Wert der length\-Eigenschaft stets um eins größer als der höchste Index im Array.  
  
## String\-Objekt  
 In [!INCLUDE[javascript](../includes/javascript-md.md)] können Sie Zeichenfolgen \(und Zahlen\) so behandeln als wären es Objekte.  Das [string\-Objekt](../javascript/reference/string-object-javascript.md) verfügt über bestimmte integrierte Methoden, die Sie mit Zeichenfolgen verwenden können.  Eine dieser Methoden ist die [substring\-Methode](../javascript/reference/substring-method-string-javascript.md), die einen Teil der Zeichenfolge zurückgibt.  Der Methode werden zwei Zahlen als Argumente übergeben.  
  
```javascript  
var aString = "0123456789";  
  
// This code sets aChunk to "456".  
var aChunk = aString.substring(4, 7);  
  
// This code sets anotherChunk to "456", using  
// the lower value index as the starting index.  
var anotherChunk = aString.substring(7, 4);  
  
// This code sets the firstLetter variable to "J"  
// by using the array in the preceding array creation example.  
firstLetter = theMonths[5].substring(0,1);  
```  
  
 Eine andere Eigenschaft des `String`\-Objekts ist die **length**\-Eigenschaft.  Diese Eigenschaft enthält die Anzahl der Zeichen in der Zeichenfolge \(0 bei einer leeren Zeichenfolge\).  Diese ist ein numerischer Wert, der direkt in Berechnungen verwendet werden kann.  
  
```javascript  
var howLong = "Hello World".length  // Sets the howLong variable to 11.  
```  
  
## Math\-Objekt  
 Das **Math**\-Objekt verfügt über eine Reihe vordefinierter Konstanten und Funktionen.  Die Konstanten sind spezifische Zahlen.  Eine dieser spezifischen Zahlen ist der Wert von Pi \(näherungsweise 3,14159...\).  Dies ist die **Math.PI**\-Konstante, die im folgenden Beispiel gezeigt wird.  
  
```javascript  
var radius = 5;  
var circleArea = Math.PI * radius * radius;  
```  
  
 Eine der integrierten Funktionen des **Math**\-Objekts ist die Potenzierungs\- bzw. `Math.pow`\-Methode, die eine Zahl mit einem bestimmten Exponenten potenziert.  Im folgenden Beispiel werden sowohl Pi als auch die Potenzierung verwendet, um das Volumen einer Kugel zu berechnen.  
  
```javascript  
var volume = (4/3)*(Math.PI*Math.pow(radius,3));  
```  
  
## Date\-Objekt  
 Mit dem `Date`\-Objekt können beliebige Datums\- und Uhrzeitangaben dargestellt, das aktuelle Systemdatum abgerufen und die Zeit zwischen Datumsangaben berechnet werden.  Es verfügt über mehrere vordefinierte Eigenschaften und Methoden.  Im Allgemeinen stellt das `Date`\-Objekt den Wochentag, den Monat, den Tag und das Jahr sowie die Uhrzeit in Stunden, Minuten und Sekunden bereit.  Diese Informationen basieren auf der Anzahl von Millisekunden seit dem 1. Januar 1970, 00:00: 00,000 GMT, d. h. Greenwich Mean Time \(der bevorzugte Begriff lautet UTC oder „Universal Coordinated Time“ bzw. koordinierte Weltzeit und bezieht sich auf die vom Weltzeitstandard ausgegebenen Signale\).  [!INCLUDE[javascript](../includes/javascript-md.md)] kann Datumsangaben verarbeiten, die ungefähr im Bereich von 250.000 v. Chr.  bis 255.000 n. Chr. liegen.  
  
 Um ein neues `Date`\-Objekt zu erstellen, verwenden Sie den **new**\-Operator, wie im folgenden Beispiel gezeigt.  
  
```javascript  
var toDay = new Date();    
var thisYear = toDay.getFullYear();  
var thisMonth = theMonths[toDay.getMonth()];  
var thisDay = thisMonth  + " " + toDay.getDate() + ", " + thisYear;  
```  
  
## Number\-Objekt  
 Zusätzlich zu den speziellen numerischen Konstanten \(z. B. `PI`\), die im **Math**\-Objekt verfügbar sind, sind einige andere Konstanten in [!INCLUDE[javascript](../includes/javascript-md.md)] über das **Number**\-Objekt verfügbar.  
  
|Konstante|Beschreibung|  
|---------------|------------------|  
|Number.MAX\_VALUE|Größte darstellbare Zahl, ungefähr 1,79E\+308; kann positiv oder negativ sein.  \(Der Wert variiert leicht von System zu System.\)|  
|Number.MIN\_VALUE|Kleinste darstellbare Zahl, ungefähr 5.00E\-324; kann positiv oder negativ sein.  \(Der Wert variiert leicht von System zu System.\)|  
|Number.NaN|Spezieller nicht numerischer Wert, „Not a Number“ \(keine Zahl\).|  
|Number.POSITIVE\_INFINITY|Jeder positive Wert, der größer als die größte positive Zahl \(Number.MAX\_VALUE\) ist, wird automatisch in diesen Wert konvertiert; dargestellt als plus unendlich.|  
|Number.NEGATIVE\_INFINITY|Jeder Wert, der kleiner als die kleinste negative Zahl \(\-Number.MAX\_VALUE\) ist, wird automatisch in diesen Wert konvertiert; dargestellt als minus unendlich.|  
  
 **Number.NaN** ist eine spezielle Konstante, die als „Not a Number“ \(keine Zahl\) definiert ist. Beim Versuch, eine Zeichenfolge zu analysieren, die nicht als Zahl analysiert werden kann, wird **Number.NaN** zurückgegeben.  Der Vergleich von `NaN` ergibt eine Ungleichheit mit allen Zahlen und sich selbst.  Um ein `NaN`\-Ergebnis zu testen, führen Sie keinen Vergleich mit **Number.NaN** durch, sondern verwenden Sie stattdessen die Funktion **isNaN\(\)**.  
  
## JSON\-Objekt  
 JSON ist ein einfaches Datenaustauschformat, das auf einem Teil der Objektliteralnotation der Programmiersprache JavaScript basiert.  
  
 Das JSON\-Objekt stellt zwei Funktionen zum Konvertieren in das und aus dem JSON\-Textformat bereit.  Die Funktion [JSON.stringify](../javascript/reference/json-stringify-function-javascript.md) serialisiert Objekte und Arrays in JSON Text.  Die [JSON.parse](../javascript/reference/json-parse-function-javascript.md)\-Funktion deserialisiert JSON\-Text, um Objekte im Arbeitsspeicher zu erzeugen.  Weitere Informationen finden Sie unter [Einführung in JavaScript Object Notation \(JSON\) in JavaScript und .NET](http://go.microsoft.com/fwlink/?LinkId=124098).  
  
## Siehe auch  
 [JavaScript\-Objekte](../javascript/reference/javascript-objects.md)
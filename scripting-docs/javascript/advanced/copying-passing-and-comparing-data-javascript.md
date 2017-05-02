---
title: "Kopieren, &#220;bergeben und Vergleichen von Daten (JavaScript) | Microsoft Docs"
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
  - "Arrays [Visual Basic], Kopieren von Daten"
  - "Arrays [Visual Basic], Übergeben von Werten"
  - "Arrays [Visual Basic], Datentypen festlegen"
  - "ByRef-Argument"
  - "ByVal-Argument"
  - "Funktionsparameter"
  - "Funktionsparameter, Informationen über Funktionsparameter"
  - "Zeichenfolgenvergleich"
  - "Zeichenfolgenvergleich, Daten testen"
ms.assetid: fbccd877-7249-45d4-bd9f-6bcd8ba94a6b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Kopieren, &#220;bergeben und Vergleichen von Daten (JavaScript)
Die Verarbeitung von Daten in [!INCLUDE[javascript](../../includes/javascript-md.md)] hängt vom Datentyp ab.  
  
## Nach Wert oder Nach Verweis  
 Zahlen und boolesche Werte \(**true** und **false**\) werden *nach Wert* kopiert, übergeben und verglichen.  Beim Kopieren oder Übergeben nach Wert belegen Sie Speicherplatz auf dem Computer und kopieren den Wert des Originals dorthin.  Wenn Sie dann das Original ändern, ist die Kopie davon nicht betroffen \(und umgekehrt\), da es sich um zwei getrennte Entitäten handelt.  
  
 Objekte, Arrays und Funktionen werden *nach Verweis* kopiert, übergeben und verglichen.  Beim Kopieren oder Übergeben nach Verweis erstellen Sie im Grunde einen Zeiger auf das ursprüngliche Element und verwenden den Zeiger, als ob er eine Kopie wäre.  Wenn Sie dann das ursprüngliche Element ändern, werden sowohl das Original als auch die Kopie \(und umgekehrt\) geändert.  Tatsächlich ist jedoch nur eine Entität vorhanden, denn die Kopie ist keine wirkliche Kopie, sondern nur ein Verweis auf die Daten.  
  
 Beim Vergleichen nach Verweis müssen die beiden Variablen exakt auf die gleiche Entität verweisen, damit der Vergleich erfolgreich ist.  Beispielsweise sind zwei unterschiedliche **Array**\-Objekte bei einem Vergleich immer ungleich, auch wenn sie dieselben Elemente enthalten.  Eine der Variablen muss ein Verweis auf die andere Variable sein, damit der Vergleich erfolgreich durchgeführt werden kann.  Vergleichen Sie die Ergebnisse der **toString\(\)**\-Methode, um zu prüfen, ob zwei Arrays dieselben Elemente enthalten.  
  
 Zeichenfolgen werden nach Verweis kopiert und übergeben, aber nach Wert verglichen.  Zwei **String**\-Objekte \(erstellt mit **new** String \("xyz"\)\), werden nach Verweis miteinander verglichen, aber wenn einer oder beide der Werte ein Zeichenfolgenwert ist, werden sie nach Wert miteinander verglichen.  
  
> [!NOTE]
>  Der ASCII\- und der ANSI\-Zeichensatz sind so aufgebaut, dass Großbuchstaben vor Kleinbuchstaben rangieren.  So ist bei einem Vergleich "Zoo" *kleiner* als "adler". Sie können **toUpperCase\(\)** oder **toLowerCase\(\)** für beide Zeichenfolgen aufrufen, wenn Sie einen Vergleich ohne Berücksichtigung von Groß\- und Kleinschreibung durchführen möchten.  
  
## Übergeben von Parametern an Funktionen  
 Wenn Sie einen Parameter nach Wert an eine Funktion übergeben, wird eine separate Kopie dieses Parameters erstellt, die nur innerhalb der Funktion vorhanden ist.  Wenn Sie Objekte und Arrays in der Funktion mit einem neuen Wert überschreiben, wird der neue Wert wird nicht außerhalb der Funktion widergespiegelt, obwohl Objekte und Arrays nach Verweis übergeben werden.  Nur Änderungen an den Eigenschaften von Objekten oder an Elementen von Arrays sind außerhalb der Funktion sichtbar.  
  
 Beispiel \(mit dem Internet Explorer\-Objektmodell\):  
  
```javascript  
// This clobbers (over-writes) its parameter, so the change  
// is not reflected in the calling code.  
function Clobber(param)   
{  
    // clobber the parameter; this will not be seen in   
    // the calling code  
    param = new Object();  
    param.message = "This will not work";  
}  
  
// This modifies a property of the parameter, which  
// can be seen in the calling code.  
function Update(param)  
{  
    // Modify the property of the object; this will be seen  
    // in the calling code.  
    param.message = "I was changed";  
}  
  
// Create an object, and give it a property.  
var obj = new Object();  
obj.message = "This is the original";  
  
// Call Clobber, and print obj.message. Note that it hasn't changed.  
Clobber(obj);  
window.alert(obj.message); // Still displays "This is the original".  
  
// Call Update, and print obj.message. Note that is has changed.  
Update(obj);  
window.alert(obj.message); // Displays "I was changed".  
```  
  
## Testen von Daten  
 Wenn Sie einen Test nach Wert durchführen, werden zwei unterschiedliche Elemente miteinander verglichen, um festzustellen, ob sie gleich sind.  In der Regel wird dieser Vergleich byteweise durchgeführt.  Wenn Sie einen Test nach Verweis durchführen, möchten Sie prüfen, ob zwei Elemente Zeiger auf ein einzelnes ursprüngliches Element sind.  Ist dies der Fall, sind die Elemente gleich. Andernfalls sind sie nicht gleich, selbst wenn sie die gleichen Werte enthalten.  
  
 Das Kopieren und Übergeben von Zeichenfolgen nach Verweis spart Speicherplatz. Da Zeichenfolgen nach dem Erstellen nicht änderbar sind, können sie nach Wert verglichen werden.  Dadurch können Sie überprüfen, ob zwei Zeichenfolgen denselben Inhalt aufweisen, selbst wenn eine vollständig separat von der anderen generiert wurde.  
  
## Siehe auch  
 [Berechnen von Datum und Uhrzeit \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)
---
title: "Problembehandlung bei Skripts (JavaScript) | Microsoft Docs"
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
  - "Automatische Typkonvertierung"
  - "Problembehandlung bei Skripts"
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Problembehandlung bei Skripts (JavaScript)
In jeder Programmiersprache gibt es Stellen, die Überraschungen bereit halten.  So verhält sich beispielsweise der `null`\-Wert in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nicht wie die gleiche `Null`\-Wert in den Programmiersprachen C oder C\+\+.  
  
 Im Folgenden werden einige mögliche Problembereiche beim Schreiben von Skripts in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] erörtert.  
  
## Syntaxfehler  
 Beim Schreiben von Skripts ist es wichtig, Details zu beachten.  So müssen z. B. Zeichenfolgen in Anführungszeichen eingeschlossen werden.  
  
## Reihenfolge der Skriptinterpretation  
 Die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Interpretation ist Teil des HTML\-Analyseprozesses des Webbrowsers.  Wenn Sie ein Skript innerhalb des \<HEAD\>\-Tags eines Dokuments platzieren, wird dieses vor allen Teilen des \<BODY\>\-Tags interpretiert.  Wenn Sie über Objekte verfügen, die im \<BODY\>\-Tag erstellt wurden, sind diese zum Zeitpunkt der \<HEAD\>\-Analyse nicht vorhanden, und können nicht vom Skript bearbeitet werden.  
  
> [!NOTE]
>  Dieses Verhalten ist spezifisch für Internet Explorer.  ASP und WSH verfügen über andere Ausführungsmodelle \(wie auch andere Hosts\).  
  
## Automatische Typumwandlung  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ist eine Sprache mit flexibler Typbindung und automatischer Umwandlung.  Obwohl die Werte mit verschiedenen Typen nicht identisch sind, werden die Ausdrücke im folgenden Beispiel zu **true** ausgewertet.  
  
```javascript  
"100" == 100;  
false == 0;  
```  
  
 Verwenden Sie den strikten Gleichheitsoperator \(\=\=\=\), um zu überprüfen, ob Typ und Wert identisch sind.  Die folgenden Ausdrücke werden beide als "false" ausgewertet:  
  
```javascript  
"100" === 100;  
false === 0;  
```  
  
## Operatorrangfolge  
 Die [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md) bestimmt, wann ein Vorgang während der Auswertung eines Ausdrucks ausgeführt wird.  Im folgenden Beispiel wird die Multiplikation vor der Subtraktion durchgeführt, obwohl die Subtraktion im Ausdruck weiter vorne vorkommt.  
  
```javascript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## Verwenden von "for...in"\-Schleifen mit Objekten  
 Wenn in einem Skript die Eigenschaften eines Objekts mit einer [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)\-Schleife durchlaufen werden, können Sie die Reihenfolge, in der die Felder des Objekts der Schleifenzählvariablen zugewiesen werden, nicht vorhersagen oder steuern.  Darüber hinaus kann die Reihenfolge in verschiedenen Implementierungen der Sprache unterschiedlich sein.  
  
## with\-Schlüsselwort  
 Das [with](../../javascript/reference/with-statement-javascript.md)\-Schlüsselwort ist nützlich zum Ansprechen von Eigenschaften, die in einem bestimmten Objekt bereits vorhanden sind. Sie kann jedoch nicht verwendet werden, um Eigenschaften zu einem Objekt hinzuzufügen.  Wenn Sie neue Eigenschaften in einem Objekt erstellen möchten, müssen Sie ausdrücklich auf das Objekt verweisen.  
  
## this\-Schlüsselwort  
 Obwohl Sie das `this`\-Schlüsselwort innerhalb der Definition eines Objekts verwenden, um auf das Objekt selbst zu verweisen, können Sie `this` oder ähnliche Schlüsselwörter nicht verwenden, um auf die gegenwärtig ausgeführte Funktion zu verweisen, wenn diese Funktion keine Objektdefinition ist.  Wenn die Funktion einem Objekt als Methode zugewiesen werden soll, können Sie das `this`\-Schlüsselwort innerhalb der Funktion verwenden, um auf das Objekt zu verweisen.  
  
## Schreiben eines Skriptes, das ein Skript in Internet Explorer schreibt  
 Das \<\/SCRIPT\>\-Tag beendet das aktuelle Skript, wenn der Interpreter darauf trifft.  Um "\<\/SCRIPT\>" selbst anzuzeigen, schreiben Sie dieses Tag als mindestens zwei Zeichenfolgen um, z. B. als "\<\/SCR" und "IPT\>", die Sie danach in der Anweisung, die diese schreibt, miteinander verketten können.  
  
## Implizite Fensterverweise in Internet Explorer  
 Da zu einem Zeitpunkt mehrere Fenster geöffnet sein können, zeigt jeder implizite Fensterverweis auf das aktuelle Fenster.  Für andere Fenster müssen Sie explizite Verweise verwenden.
---
title: "name-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "name"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Name-Eigenschaft"
  - "name-Eigenschaft, Fehlerbezeichnung"
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# name-Eigenschaft (Fehler) (JavaScript)
Gibt den Namen eines Fehlers zurück.  
  
## Syntax  
  
```  
  
errorObj.  
name  
  
```  
  
## Parameter  
 `errorObj`  
 Erforderlich.  Instanz eines `Error`\-Objekts.  
  
## Hinweise  
 Die **name**\-Eigenschaft gibt den Namen oder den Ausnahmetyp eines Fehlers zurück.  Wenn ein Laufzeitfehler auftritt, wird die name\-Eigenschaft auf einen der folgenden systemeigenen Ausnahmetypen festgelegt:  
  
|Ausnahmetyp|Bedeutung|  
|-----------------|---------------|  
|ConversionError|Dieser Fehler tritt immer dann auf, wenn versucht wird, ein Objekt in etwas zu konvertieren, in das es nicht konvertiert werden kann.|  
|RangeError|Dieser Fehler tritt auf, wenn einer Funktion ein Argument übergeben wird, das nicht im zulässigen Bereich liegt.  Beispielsweise tritt dieser Fehler auf, wenn Sie versuchen, ein `Array`\-Objekt mit einer Länge zu erstellen, die keine gültige positive ganze Zahl ist.|  
|ReferenceError|Dieser Fehler tritt auf, wenn ein ungültiger Verweis gefunden wurde.  Der Fehler wird beispielsweise ausgegeben, wenn ein erwarteter Verweis `null` ist.|  
|RegExpError|Dieser Fehler tritt auf, wenn bei einem regulären Ausdruck ein Kompilierungsfehler auftritt.  Nachdem der reguläre Ausdruck kompiliert wurde, kann dieser Fehler jedoch nicht auftreten.  Beispielsweise tritt der Fehler auf, wenn ein regulärer Ausdruck mit einem Muster deklariert wird, das eine ungültige Syntax aufweist, oder wenn er mit anderen Flags als **i**, **g** oder **m** deklariert wird bzw. mehrmals das gleiche Flag enthält.|  
|SyntaxError|Dieser Fehler tritt auf, wenn Quelltext analysiert wird und nicht die richtige Syntax besitzt.  Beispielsweise tritt der Fehler auf, wenn die `eval`\-Funktion mit einem Argument aufgerufen wird, das kein gültiger Programmtext ist.|  
|TypeError|Dieser Fehler tritt immer dann auf, wenn der tatsächliche Typ eines Operanden nicht dem erwarteten Typ entspricht.  Ein Beispiel für das Auftreten dieses Fehlers ist ein Funktionsaufruf für etwas, das kein Objekt ist oder den Aufruf nicht unterstützt.|  
|URIError|Dieser Fehler tritt auf, wenn ein unzulässiger URI \(Uniform Resource Indicator\) gefunden wird.  Beispielsweise tritt dieser Fehler auf, wenn in einer zu codierenden oder zu decodierenden Zeichenfolge ein ungültiges Zeichen gefunden wird.|  
  
## Beispiel  
 Im folgenden Beispiel werden eine TypeError\-Ausnahme ausgelöst und der Name des Fehlers und die zugehörige Meldung angezeigt.  
  
```javascript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## Beispiel  
 Dieser Code generiert die folgende Ausgabe.  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [Error\-Objekt](../../javascript/reference/error-object-javascript.md)  
  
## Siehe auch  
 [description\-Eigenschaft \(Fehler\)](../../javascript/reference/description-property-error-javascript.md)   
 [message\-Eigenschaft \(Fehler\)](../../javascript/reference/message-property-error-javascript.md)   
 [number\-Eigenschaft \(Fehler\)](../../javascript/reference/number-property-error-javascript.md)
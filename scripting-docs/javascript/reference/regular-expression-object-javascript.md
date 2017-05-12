---
title: "Regular&#160;Expression-Objekt (JavaScript) | Microsoft Docs"
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
  - "RegularExpression_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp-Objekt, Übersicht"
  - "Regular Expression-Objekt"
  - "Reguläre Ausdrücke, RegExp-Objekt"
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Regular&#160;Expression-Objekt (JavaScript)
Ein Objekt, das ein Muster eines regulären Ausdrucks sowie Flags enthält, die kennzeichnen, wie das Muster angewendet werden soll.  
  
## Syntax  
  
```  
re = /pattern/[flags]  
```  
  
## Syntax  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## Parameter  
 *re*  
 Erforderlich.  Der Variablenname, dem das Muster eines regulären Ausdrucks zugewiesen wird.  
  
 *pattern*  
 Erforderlich.  Das zu verwendende Muster eines regulären Ausdrucks.  Wenn Sie Syntax 1 verwenden, trennen Sie das Muster mit dem Zeichen "\/" ab.  Wenn Sie Syntax 2 verwenden, schließen Sie das Muster in Anführungszeichen ein.  
  
 `flags`  
 Dies ist optional.  Schließen Sie Flags in Anführungszeichen ein, wenn Sie Syntax 2 verwenden.  Folgende Flags, die miteinander kombinierbar sind, stehen zur Verfügung:  
  
-   g \(globale Suche nach allen Vorkommen von *pattern*\)  
  
-   i \(Groß\-\/Kleinschreibung ignorieren\)  
  
-   m \(mehrzeilige Suche\)  
  
-   u \(Unicode\), aktiviert EcmaScript 6\-[Unicode\-Funktionen](../../javascript/advanced/special-characters-javascript.md).  Wird nur in [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] unterstützt.  
  
-   y \(Übereinstimmung\) sucht nach Übereinstimmungen in der `lastIndex`\-Eigenschaft des regulären Ausdrucks \(und sucht nicht in späteren Indizes\).  Wird in [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] unterstützt.  
  
## Hinweise  
 Das **Regular Expression**\-Objekt sollte nicht mit dem globalen `RegExp`\-Objekt verwechselt werden.  Es sieht so aus, als wären es dieselben Objekte, sie sind jedoch verschieden.  Die Eigenschaften des **Regular Expression**\-Objekts enthalten nur Informationen über eine bestimmte **Regular Expression**\-Instanz, während die Eigenschaften des globalen `RegExp`\-Objekts ständig aktualisierte Informationen über jede aufgetretene Übereinstimmung enthalten.  
  
 **Regular Expression**\-Objekte speichern Muster, die für das Durchsuchen von Zeichenfolgen nach Zeichenkombinationen verwendet werden.  Nach dem Erstellen des **Regular Expression**\-Objekts wird dieses entweder an eine string\-Methode übergeben, oder eine Zeichenfolge wird an eine der regular expression\-Methoden übergeben.  Informationen zur zuletzt durchgeführten Suche werden im globalen `RegExp`\-Objekt gespeichert.  
  
 Verwenden Sie Syntax 1, wenn Ihnen die zu suchende Zeichenfolge vorher bekannt ist.  Verwenden Sie Syntax 2, wenn sich die Suchzeichenfolge häufig ändert oder unbekannt ist, z. B. Zeichenfolgen, die von einer Benutzereingabe abgeleitet werden.  
  
 Das *pattern*\-Argument wird vor der Verwendung in ein internes Format kompiliert.  Bei Syntax 1 wird *pattern* beim Laden des Skripts kompiliert.  Bei Syntax 2 wird *pattern* kurz vor der Verwendung bzw. beim Aufrufen der **compile**\-Methode kompiliert.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung des **Regular Expression**\-Objekts, indem ein Objekt \(re\) erstellt wird, das ein Muster eines regulären Ausdrucks mit den zugeordneten Flags enthält.  In diesem Fall wird das resultierende **Regular Expression**\-Objekt anschließend von der `match`\-Methode verwendet:  
  
```javascript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## Beispiel  
 Im folgenden Beispiel wird das Muster eines regulären Ausdrucks für die Suche nach mehreren Instanzen aktualisiert:  
  
```javascript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## Beispiel  
 Wird bei Verwendung des \/y\-Flags eine Übereinstimmung ermittelt, wird `lastindex` auf den Index des nächsten Zeichens nach der letzten Übereinstimmung aktualisiert.  Wird keine Übereinstimmung ermittelt, wird `lastindex` auf 0 zurückgesetzt.  
  
 Im folgenden Beispiel wird mit dem \/y\-Flag und der `lastIndex`\-Eigenschaft in einem bestimmten Index nach einer Übereinstimmung gesucht.  
  
```javascript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## Eigenschaften  
 [global\-Eigenschaft](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [ignoreCase\-Eigenschaft](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [multiline\-Eigenschaft](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [source\-Eigenschaft](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## Methoden  
 [compile\-Methode](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [exec\-Methode](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [test\-Methode](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 Das u\-Flag wird in [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] unterstützt.  
  
 Das y\-Flag wird in [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] unterstützt.  
  
## Siehe auch  
 [RegExp\-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)
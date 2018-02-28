---
title: Regular Expression-Objekt (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RegularExpression_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Regular Expression object
- regular expressions, RegExp object
- RegExp object, overview
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2d07e3b47e315ec804e5a7f20024dc2184eef0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-javascript"></a>Regular Expression-Objekt (JavaScript)
Ein Objekt, das ein Muster eines regulären Ausdrucks sowie Flags enthält, die kennzeichnen, wie das Muster angewendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
re = /pattern/[flags]  
```  
  
## <a name="syntax"></a>Syntax  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## <a name="parameters"></a>Parameter  
 *RE*  
 Erforderlich. Der Variablenname, dem das Muster eines regulären Ausdrucks zugewiesen wird.  
  
 *Muster*  
 Erforderlich. Das zu verwendende Muster eines regulären Ausdrucks. Wenn Sie Syntax 1 verwenden, trennen Sie das Muster mit dem Zeichen "/" ab. Wenn Sie Syntax 2 verwenden, schließen Sie das Muster in Anführungszeichen ein.  
  
 `flags`  
 Dies ist optional. Schließen Sie Flags in Anführungszeichen ein, wenn Sie Syntax 2 verwenden. Folgende Flags, die miteinander kombinierbar sind, stehen zur Verfügung:  
  
-   g (globale Suche nach allen Vorkommen von *Muster*)  
  
-   i (Groß-/Kleinschreibung ignorieren)  
  
-   m (mehrzeilige Suche)  
  
-   u (Unicode), aktiviert EcmaScript 6- [Unicode-Funktionen](../../javascript/advanced/special-characters-javascript.md). Wird nur in [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] unterstützt.  
  
-   y (Übereinstimmung) sucht nach Übereinstimmungen in der `lastIndex`-Eigenschaft des regulären Ausdrucks (und sucht nicht in späteren Indizes). Wird in [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] unterstützt.  
  
## <a name="remarks"></a>Hinweise  
 Die **reguläre** Objekt sollte nicht mit dem globalen verwechselt werden `RegExp` Objekt. Es sieht so aus, als wären es dieselben Objekte, sie sind jedoch verschieden. Die Eigenschaften der **reguläre** -Objekts enthalten nur Informationen über eine bestimmte **reguläre** Instanz, während die Eigenschaften des globalen `RegExp` Objekt enthalten Informationen über jede Übereinstimmung ständig aktualisiert, während es eintritt.  
  
 **Reguläre Ausdrücke** -Objekte speichern Muster, die beim Suchen von Zeichenfolgen für Zeichenkombinationen verwendet. Nach der **reguläre** Objekt erstellt wird, entweder an eine String-Methode übergeben oder eine Zeichenfolge an eine der Methoden für reguläre Ausdrücke übergeben wird. Informationen zur zuletzt durchgeführten Suche werden im globalen `RegExp`-Objekt gespeichert.  
  
 Verwenden Sie Syntax 1, wenn Ihnen die zu suchende Zeichenfolge vorher bekannt ist. Verwenden Sie Syntax 2, wenn sich die Suchzeichenfolge häufig ändert oder unbekannt ist, z. B. Zeichenfolgen, die von einer Benutzereingabe abgeleitet werden.  
  
 Die *Muster* Argument in ein internes Format vor der Verwendung kompiliert wird. Bei Syntax 1 wird *Muster* Laden des Skripts kompiliert wird. Bei Syntax 2 wird *Muster* unmittelbar vor der Verwendung kompiliert wird oder wenn die **Kompilieren** -Methode aufgerufen wird.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **reguläre** Objekt, indem Sie ein Objekt (RE) erstellt, die Muster eines regulären Ausdrucks mit den zugeordneten Flags enthält. In diesem Fall wird die resultierende **reguläre** Objekt wird dann verwendet, durch die `match` Methode:  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Muster eines regulären Ausdrucks für die Suche nach mehreren Instanzen aktualisiert:  
  
```JavaScript  
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
  
## <a name="example"></a>Beispiel  
 Wird bei Verwendung des /y-Flags eine Übereinstimmung ermittelt, wird `lastindex` auf den Index des nächsten Zeichens nach der letzten Übereinstimmung aktualisiert. Wird keine Übereinstimmung ermittelt, wird `lastindex` auf 0 zurückgesetzt.  
  
 Im folgenden Beispiel wird mit dem /y-Flag und der `lastIndex`-Eigenschaft in einem bestimmten Index nach einer Übereinstimmung gesucht.  
  
```JavaScript  
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
## <a name="properties"></a>Eigenschaften  
 [Global-Eigenschaft](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [IgnoreCase-Eigenschaft](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [multiline-Eigenschaft](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [source-Eigenschaft](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## <a name="methods"></a>Methoden  
 [Compile-Methode](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [Exec-Methode](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [test-Methode](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 Das u-Flag wird in [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] unterstützt.  
  
 Das y-Flag wird in [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)] unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [RegExp-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String-Objekt](../../javascript/reference/string-object-javascript.md)
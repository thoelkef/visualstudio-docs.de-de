---
title: Replace-Methode (String) (JavaScript) | Microsoft Docs
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
- replace
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- replacing strings
- Replace method
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82894a5d7f92c8231a6ba3a1948369fb2c819a6d
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="replace-method-string-javascript"></a>replace-Methode (String) (JavaScript)
Ersetzt Text in einer Zeichenfolge unter Verwendung eines regulären Ausdrucks oder einer Suchzeichenfolge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
stringObj.replace(rgExp, replaceText)  
```  
  
## <a name="parameters"></a>Parameter  
 `stringObj`  
 Erforderlich. Das `String`-Objekt oder -Zeichenfolgenliteral, in dem die Ersetzung ausgeführt werden soll. Diese Zeichenfolge wird nicht geändert, indem die **ersetzen** Methode. Stattdessen ist der Rückgabewert dieser Methode die Zeichenfolge, die durch die Ersetzung erzeugt wird.  
  
 `rgExp`  
 Erforderlich. Eine Instanz von einem **reguläre** Objekt, das das Muster eines regulären Ausdrucks sowie anwendbare Flags enthält. Kann auch ein `String`-Objekt oder -Zeichenfolgenliteral sein, das den regulären Ausdruck darstellt. Wenn `rgExp` ist keine Instanz von einem **reguläre** -Objekt, wird es in eine Zeichenfolge konvertiert und eine exakte Suche nach den Ergebnissen durchgeführt wird, wird kein Versuch unternommen, um die Zeichenfolge in einem regulären Ausdruck zu konvertieren.  
  
 `replaceText`  
 Erforderlich. Ein `String`-Objekt oder -Zeichenfolgenliteral, das den Text enthält, der jede Übereinstimmung von `rgExp` in `stringObj` ersetzen soll. In [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher kann das `replaceText`-Argument auch eine Funktion sein, die den Ersetzungstext zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Das Ergebnis der **ersetzen** Methode ist eine Kopie des `stringObj` nachdem die angegebenen Ersetzungen durchgeführt wurden.  
  
## <a name="remarks"></a>Hinweise  
 Jede der folgenden Übereinstimmungsvariablen kann zum Identifizieren der aktuellsten Übereinstimmung und der Zeichenfolge, aus der sie resultierte, verwendet werden. Die Übereinstimmungsvariablen können bei Textersetzungen verwendet werden, bei denen die Ersetzungszeichenfolge dynamisch bestimmt werden muss.  
  
|Zeichen|Bedeutung|  
|----------------|-------------|  
|**$$**|`$` ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher)|  
|**$&**|Gibt diesen Teil von `stringObj` an, der mit dem gesamten Muster übereinstimmt. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher)|  
|`$``|Gibt den Teil des `stringObj` , die die beschriebenen Übereinstimmung vorangestellt  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher)|  
|`$'`|Gibt den Teil des `stringObj` , folgt die Übereinstimmung von beschriebenen  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher)|  
|`$`  ***n***|Die  *n* te erfasste teilübereinstimmung, wobei  *n*  ist eine einfache Dezimalzahl zwischen 1 und 9. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher)|  
|`$`  ***nn***|Die  *nn* te erfasste teilübereinstimmung, wobei  *nn*  eine zweistellige Dezimalzahl zwischen 01 und 99 ist. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] oder höher)|  
  
 Wenn `replaceText` ist eine Funktion für jede übereinstimmende untergeordnete Zeichenfolge die Funktion, mit den folgenden aufgerufen wird *m* Argumenten + 3, in denen *m* ist die Anzahl von links schließenden Klammern in der `rgExp`. Das erste Argument ist die übereinstimmende untergeordnete Zeichenfolge. Das nächste *m* -Argumente sind alle Erfassungen, die von der Suche resultieren. Argument *m* + 2 ist der Offset in `stringObj` , in dem die Übereinstimmung auftrat, und das Argument *m* + 3 ist `stringObj`. Das Ergebnis ist eine Zeichenfolge, die daraus resultiert, dass jede übereinstimmende untergeordnete Zeichenfolge durch den entsprechenden Rückgabewert des Funktionsaufrufs ersetzt wird.  
  
 Die **ersetzen** -Methode aktualisiert die Eigenschaften des globalen `RegExp` Objekt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **ersetzen** -Methode zum Ersetzen aller Instanzen von "the" durch "a".  
  
```JavaScript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 Darüber hinaus die **ersetzen** kann-Methode Teilausdrücke im Muster ersetzt. Im folgenden Beispiel wird jedes Paar von Wörtern in der Zeichenfolge ausgetauscht.  
  
```JavaScript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumped lazy the dog.  
```  
  
 Im folgenden Beispiel, das in [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] und höher ausgeführt werden kann, wird die Verwendung einer Funktion gezeigt, die den Ersatztext zurückgibt. Sie ersetzt jede Instanz einer Zahl, auf die „F“ folgt, durch eine Celsiuskonvertierung.  
  
```JavaScript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Exec-Methode (regulärer Ausdruck)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Match-Methode (String)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [Search-Methode (String)](../../javascript/reference/search-method-string-javascript.md)   
 [Test-Methode (regulärer Ausdruck)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmieren mit regulären Ausdrücken (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternierung und Unterausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Rückverweise (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [HTML5 Drag & drop-Beispiel-app](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)
---
title: HTML-Tag-Methode (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- link method [JavaScript]
- blink method [JavaScript]
- fontsize method [JavaScript]
- italics method [JavaScript]
- sup method [JavaScript]
- anchor method [JavaScript]
- fixed method [JavaScript]
- fontcolor method [JavaScript]
- bold method [JavaScript]
- small method [JavaScript]
- HTML Tag methods [JavaScript]
- sub method [JavaScript]
- big method [JavaScript]
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7639bc609d8e9b7e4b212fe67ae40f81487d708e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638650"
---
# <a name="html-tag-methods-javascript"></a>HTML-Tag-Methode (JavaScript)
Sie können HTML-Tag-Methoden zum Platzieren von HTML-Elemente, um Text in einem `String` Objekt.  
  
## <a name="syntax"></a>Syntax  
 Die folgende Tabelle enthält die Syntax für und eine Beschreibung der einzelnen HTML-Tag-Methoden.  
  
 In der Spalte Syntax `string1` ist ein `String` -Objekt oder Zeichenfolgenliteral.  
  
 Die Standard-Spalte gibt an [World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?LinkId=199553) Empfehlungen für HTML 4. "Abgeraten" gibt an, dass das HTML-Element zugunsten von Stylesheets abgeraten wird.  
  
|Syntax|Methodenbeschreibung|Beschreibung des Parameters|Standard|  
|------------|------------------------|---------------------------|--------------|  
|`string1`.Anchor (`name`)|Platziert einen HTML-Anker mit einem NAME-Attribut, um den Text an.|Die `name` Parameter ist der Text in das Namensattribut des HTML-Anker aufgenommen werden sollen.||  
|`string1`.Big()|Fügt HTML \<BIG >-Tags den Textqualifizierer eingeschlossen.||Abgeraten|  
|`string1`.blink()|Setzt-HTML- \<BLINK >-Tags den Textqualifizierer eingeschlossen. Die \<BLINK >-Tag wird in Internet Explorer nicht unterstützt.||Nicht im standard|  
|`string1`.Bold()|Fügt HTML \<B >-Tags den Textqualifizierer eingeschlossen.||Abgeraten|  
|`string1`.Fixed()|Fügt HTML \<TT >-Tags den Textqualifizierer eingeschlossen.||Abgeraten|  
|`string1`.fontcolor (`color`)|Fügt HTML \<FONT >-Tags mit einem COLOR-Attribut den Textqualifizierer eingeschlossen.|Die `color` Parameter ist eine Zeichenfolge, die den hexadezimalen Wert oder vordefinierte Namen für eine Farbe enthält. Gültige vordefinierten Farbnamen richten sich nach der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Browser und die Version des Hosts.|Als veraltet markiert|  
|`string1`.FontSize (`size`)|Fügt HTML \<FONT >-Tags mit einem SIZE-Attribut den Textqualifizierer eingeschlossen.|Die `size` Parameter ist ein Ganzzahlwert, der die Größe des Texts angibt. Gültigen ganzzahligen Werte hängen die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Browser und die Version des Hosts.|Als veraltet markiert|  
|`string1`.italics()|Fügt HTML \<ich >-Tags den Textqualifizierer eingeschlossen.||Abgeraten|  
|`string1`.Link (`href`)|Platziert einen HTML-Anker mit einem HREF-Attribut, um den Text an.|Die `href` Parameter ist der Text in der HREF-Attribut eines HTML-Anker aufgenommen werden sollen.||  
|`string1`.Small()|Setzt-HTML- \<kleine >-Tags den Textqualifizierer eingeschlossen.||Abgeraten|  
|`string1`.Strike()|Fügt HTML \<STRIKE >-Tags den Textqualifizierer eingeschlossen.||Als veraltet markiert|  
|`string1`.Sub()|Fügt HTML \<SUB >-Tags den Textqualifizierer eingeschlossen.|||  
|`string1`.SUP()|Fügt HTML \<SUP >-Tags den Textqualifizierer eingeschlossen.|||  
  
## <a name="remarks"></a>Hinweise  
 Keine Prüfung wird ausgeführt, um festzustellen, ob die HTML-Tags in der Zeichenfolge bereits angewendet wurden.  
  
## <a name="example"></a>Beispiel  
 Die folgenden Beispiele zeigen, wie HTML-Tag-Methoden verwendet wird.  
  
```JavaScript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [String-Objekt](../../javascript/reference/string-object-javascript.md)
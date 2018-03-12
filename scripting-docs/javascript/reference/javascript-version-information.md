---
title: JavaScript-Versionsinformationen | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, version information
ms.assetid: 440f4924-f7a9-48e0-873e-bd599a93b437
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a2335c3697be9ef3e2d674ac37047ddd3de242d
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="javascript-version-information"></a>JavaScript-Versionsinformationen
Unterschiedliche Versionen von JavaScript unterstützen unterschiedliche Sätze von JavaScript-Elementen. [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -Apps unterstützen einen etwas anderen Satz von Funktionen als Internet Explorer.  
  
> [!IMPORTANT]
>  Eine [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -App ist eine neue Anwendungsart, die auf [!INCLUDE[win8](../../javascript/includes/win8-md.md)] -Geräten ausgeführt wird. Mehr über [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -Apps finden Sie unter [What's a Windows Store app?](http://msdn.microsoft.com/en-us/231c1fba-9f87-468e-94aa-45dd57edcc70)  
  
 Der Standardmodus (der bis zu Internet Explorer 11 in allen Versionen von Internet Explorer verwendete Modus, sofern die `<!doctype>` -Direktive vorhanden ist) unterstützt einen anderen Elementsatz als der Quirksmodus (der Modus, der verwendet wird, wenn keine `<!doctype>` -Direktive vorhanden ist). Weitere Informationen zur Versionsverwaltung finden Sie unter [Definieren der Dokumentkompatibilität](http://go.microsoft.com/fwlink/?LinkId=208537).  
  
 In der folgenden Tabelle werden die Dokumentmodi in Internet Explorer (und Store-Apps, die [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] und [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)]darstellen) angezeigt, die bestimmte Sprachelemente unterstützen. Dokumentmodi, die ein bestimmtes Element unterstützen, werden mit dem Buchstaben **J**angezeigt. Dokumentmodi, die kein bestimmtes Element unterstützen, werden mit dem Buchstaben **N**angezeigt.  
  
> [!IMPORTANT]
>  [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] (Edge-Browser in Windows 10) schließt nicht die Unterstützung für ältere Dokumentmodi. Unterstützung von [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)] -Apps beginnt mit Windows Phone 8.1. Experimentelle Features (zu: Flags) sind gekennzeichnet mit "exp"gekennzeichnet.  
  
 Die Tabelle enthält zusammenfassende Informationen. Genauere Informationen finden Sie in der Dokumentation für das Sprachelement  
  
|Sprachelement|Quirks, Internet Explorer 6-Standards und Internet Explorer 7-Standards|Internet Explorer 8-Standards|Internet Explorer 9-Standards|Internet Explorer 10-Standards|Internet Explorer 11-Standards|Edge|Store-Apps|  
|----------------------|--------------------------------------------------------------------------|-----------------------------------|-----------------------------------|------------------------------------|------------------------------------|----------|----------------|  
|[__proto\_ \_ -Eigenschaft (Objekt)](../../javascript/reference/proto-property-object-javascript.md)|N|N|N|N|J|J|V8 (Win): N<br />V8.1 (Win): J<br />V8.1 (Phone): J|  
|[$1...$9-Eigenschaften (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)|J|J|J|J|J|J|J|  
|[0n-Eigenschaft](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)|J|J|J|J|J|J|J|  
|[abs-Funktion](../../javascript/reference/math-abs-function-javascript.md)|J|J|J|J|J|J|J|  
|[acos-Funktion](../../javascript/reference/math-acos-function-javascript.md)|J|J|J|J|J|J|J|  
|[acosh-Funktion](../../javascript/reference/math-acosh-function-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[ActiveXObject-Objekt](../../javascript/reference/activexobject-object-javascript.md)|J|J|J|J|J|J|N|  
|[Additionszuweisungsoperator (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)|J|J|J|J|J|J|J|  
|[Additionsoperator (+)](../../javascript/reference/addition-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[apply-Methode](../../javascript/reference/apply-method-function-javascript.md)|J|J|J|J|J|J|J|  
|[arguments-Objekt](../../javascript/reference/arguments-object-javascript.md)|J|J|J|J|J|J|J|  
|[arguments-Eigenschaft](../../javascript/reference/arguments-property-function-javascript.md)|J|J|J|J|J|J|J|  
|[Array-Objekt](../../javascript/reference/array-object-javascript.md)|J|J|J|J|J|J|J|  
|[Array.from-Funktion (Array)](../../javascript/reference/array-from-function-array-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[Array.isArray-Funktion](../../javascript/reference/array-isarray-function-javascript.md)|N|N|J|J|J|J|J|  
|[Array.of-Funktion (Array)](../../javascript/reference/array-of-function-array-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[ArrayBuffer-Objekt](../../javascript/reference/arraybuffer-object.md)|N|N|N|J|J|J|J|  
|[Funktionen](../../javascript/functions-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[asin-Funktion](../../javascript/reference/math-asin-function-javascript.md)|J|J|J|J|J|J|J|  
|[Object.assign-Funktion (Objekt)](../../javascript/reference/object-assign-function-object-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[Zuweisungsoperator (=)](../../javascript/reference/assignment-operator-decrement-equal-javascript.md)|J|J|J|J|J|J|J|  
|[atan-Funktion](../../javascript/reference/math-atan-function-javascript.md)|J|J|J|J|J|J|J|  
|[atan2-Funktion](../../javascript/reference/math-atan2-function-javascript.md)|J|J|J|J|J|J|J|  
|[atEnd-Methode](../../javascript/reference/atend-method-enumerator-javascript.md)|J|J|J|J|J|J|N|  
|[bind-Methode](../../javascript/reference/bind-method-function-javascript.md)|N|N|J|J|J|J|J|  
|[Bitweiser AND-Zuweisungsoperator (&=)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)|J|J|J|J|J|J|J|  
|[Bitweiser AND-Operator (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[Bitweiser Linksschiebeoperator (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[Bitweiser NOT-Operator (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|J|J|J|J|J|J|J|  
|[Bitweiser OR -Zuweisungsoperator (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)|J|J|J|J|J|J|J|  
|[Bitweise OR-Operator (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[Bitweiser Right-Shift-Operator (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[Bitweiser YOR‑Zuweisungsoperator (^=)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)|J|J|J|J|J|J|J|  
|[Bitweiser YOR‑Operator (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|J|J|J|J|J|J|J|  
|[blink-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[bold-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[Boolean-Objekt](../../javascript/reference/boolean-object-javascript.md)|J|J|J|J|J|J|J|  
|[break-Anweisung](../../javascript/reference/break-statement-javascript.md)|J|J|J|J|J|J|J|  
|[call-Methode](../../javascript/reference/call-method-function-javascript.md)|J|J|J|J|J|J|J|  
|[callee-Eigenschaft](../../javascript/reference/callee-property-arguments-javascript.md)|J|J|J|J|J|J|J|  
|[caller-Eigenschaft](../../javascript/reference/caller-property-function-javascript.md)|J|J|J|J|J|J|J|  
|[catch-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|J|J|J|J|J|J|J|  
|[ceil-Funktion](../../javascript/reference/math-ceil-function-javascript.md)|J|J|J|J|J|J|J|  
|[charAt-Methode](../../javascript/reference/charat-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[charCodeAt-Methode](../../javascript/reference/charcodeat-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[class-Anweisung](../../javascript/reference/class-statement-javascript.md)|N|N|N|N|N|Exp.|V8.1: N<br />V10: Exp.|  
|[codePointAt-Methode (String)](../../javascript/reference/codepointat-method-string-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[Kommaoperator (,)](../../javascript/reference/comma-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[// (Einzeilige Kommentaranweisung)](../../javascript/reference/comment-statements-javascript.md)|J|J|J|J|J|J|J|  
|[/*.. \*/ (Mehrzeilige Kommentaranweisung)](../../javascript/reference/comment-statements-javascript.md)|J|J|J|J|J|J|J|  
|[Vergleichsoperatoren](../../javascript/reference/comparison-operators-javascript.md)|J|J|J|J|J|J|J|  
|[compile-Methode](../../javascript/reference/compile-method-regular-expression-javascript.md)|J|J|J|J|J|J|J|  
|[concat-Methode (Array)](../../javascript/reference/concat-method-array-javascript.md)|J|J|J|J|J|J|J|  
|[concat-Methode (String)](../../javascript/reference/concat-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)|J|J|J|J|N|N|N|  
|[Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)|J|J|J|J|N|N|N|  
|[Bedingter (ternärer) Operator (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[constructor-Eigenschaft](../../javascript/reference/constructor-property-object-javascript.md)|J|J|J|J|J|J|J|  
|[const-Anweisung](../../javascript/reference/const-statement-javascript.md)|N|N|N|N|J|J|V8 (Win): N<br />V8.1 (Win): J<br />V8.1 (Phone): J|  
|[continue-Anweisung](../../javascript/reference/continue-statement-javascript.md)|J|J|J|J|J|J|J|  
|[cos-Funktion](../../javascript/reference/math-cos-function-javascript.md)|J|J|J|J|J|J|J|  
|[create-Funktion](../../javascript/reference/object-create-function-javascript.md)|N|N|J|J|J|J|J|  
|[DataView-Objekt](../../javascript/reference/dataview-object.md)|N|N|N|J|J|J|J|  
|[Date-Objekt](../../javascript/reference/date-object-javascript.md)|J|J|J|J|J|J|J|  
|[Debugobjekt](../../javascript/reference/debug-object-javascript.md)|J|J|J|J|J|J|J|  
|[Debug.setNonUserCodeExceptions-Eigenschaft](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|J|J|J|J|  
|[Debug.setNonUserCodeExceptions-Eigenschaft](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|J|J|J|J|  
|[debugger-Anweisung](../../javascript/reference/debugger-statement-javascript.md)|J|J|J|J|J|J|J|  
|[decodeURI-Funktion](../../javascript/reference/decodeuri-function-javascript.md)|J|J|J|J|J|J|J|  
|[DecodeURIComponent-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)|J|J|J|J|J|J|J|  
|[Dekrementoperator (--)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|J|J|J|J|J|J|J|  
|[Funktionen](../../javascript/functions-javascript.md)|N|N|N|N|N|Exp.|V8.1: N<br />V10: Exp.|  
|[defineProperties-Funktion](../../javascript/reference/object-defineproperties-function-javascript.md)|N|J*|J|J|J|J|J|  
|[defineProperty-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md)|N|J*|J|J|J|J|J|  
|[delete-Operator](../../javascript/reference/delete-operator-decrementjavascript.md)|J|J|J|J|J|J|J|  
|[description-Eigenschaft](../../javascript/reference/description-property-error-javascript.md)|J|J|J|J|J|J|J|  
|[dimensions-Methode](../../javascript/reference/dimensions-method-vbarray-javascript.md)|J|J|J|J|J|J|J|  
|[Divisionszuweisungsoperator (/=)](../../javascript/reference/division-assignment-operator-decrement-equal-javascript.md)|J|J|J|J|J|J|J|  
|[Divisionsoperator (/)](../../javascript/reference/division-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[do...while-Anweisung](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)|J|J|J|J|J|J|J|  
|[E-Konstante](../../javascript/reference/math-constants-javascript.md)|J|J|J|J|J|J|J|  
|[encodeURI-Funktion](../../javascript/reference/encodeuri-function-javascript.md)|J|J|J|J|J|J|J|  
|[encodeURI-Komponentenfunktion](../../javascript/reference/encodeuricomponent-function-javascript.md)|J|J|J|J|J|J|J|  
|[entries-Methode (Array)](../../javascript/reference/entries-method-array-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[Enumeratorobjekt](../../javascript/reference/enumerator-object-javascript.md)|J|J|J|J|J|J|N|  
|[Zahlenkonstanten](../../javascript/reference/number-constants-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[Gleichheitsoperator (==)](../../javascript/reference/comparison-operators-javascript.md)|J|J|J|J|J|J|J|  
|[Error-Objekt](../../javascript/reference/error-object-javascript.md)|J|J|J|J|J|J|J|  
|[stack-Eigenschaft (Fehler)](../../javascript/reference/stack-property-error-javascript.md)|N|N|N|J|J|J|J|  
|[stackTraceLimit-Eigenschaft (Fehler)](../../javascript/reference/stacktracelimit-property-error-javascript.md)|N|N|N|J|J|J|J|  
|[escape-Funktion](../../javascript/reference/escape-function-javascript.md)|J|J|J|J|J|J|J|  
|[eval-Funktion](../../javascript/reference/eval-function-javascript.md)|J|J|J|J|J|J|J|  
|[exec-Methode](../../javascript/reference/exec-method-regular-expression-javascript.md)|J|J|J|J|J|J|J|  
|[every-Methode](../../javascript/reference/every-method-array-javascript.md)|N|N|J|J|J|J|J|  
|[exp-Funktion](../../javascript/reference/math-exp-function-javascript.md)|J|J|J|J|J|J|J|  
|[fill-Methode (Array)](../../javascript/reference/fill-method-array-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[filter-Methode](../../javascript/reference/filter-method-array-javascript.md)|N|N|J|J|J|J|J|  
|[finally-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|J|J|J|J|J|J|J|  
|[findIndex-Methode (Array)](../../javascript/reference/findindex-method-array-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[fixed-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[Float32Array-Objekt](../../javascript/reference/float32array-object.md)|N|N|N|J|J|J|J|  
|[Float64Array-Objekt](../../javascript/reference/float64array-object.md)|N|N|N|J|J|J|J|  
|[floor-Funktion](../../javascript/reference/math-floor-function-javascript.md)|J|J|J|J|J|J|J|  
|[fontcolor-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[fontsize-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[for-Anweisung](../../javascript/reference/for-statement-javascript.md)|J|J|J|J|J|J|J|  
|[forEach-Methode](../../javascript/reference/foreach-method-array-javascript.md)|N|N|J|J|J|J|J|  
|[for...in-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)|J|J|J|J|J|J|J|  
|[for...of-Anweisung](../../javascript/reference/for-dot-dot-dot-of-statement-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[freeze-Funktion](../../javascript/reference/object-freeze-function-javascript.md)|N|N|J|J|J|J|J|  
|[fromCharCode-Funktion](../../javascript/reference/string-fromcharcode-function-javascript.md)|J|J|J|J|J|J|J|  
|[fromCodePoint-Funktion](../../javascript/reference/string-fromcodepoint-function-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[Function-Objekt](../../javascript/reference/function-object-javascript.md)|J|J|J|J|J|J|J|  
|[function-Anweisung](../../javascript/reference/function-statement-javascript.md)|J|J|J|J|J|J|J|  
|[Generatoren](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Exp.|V8.1: N<br />V10: Exp.|  
|[getDate-Methode](../../javascript/reference/getdate-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getDay-Methode](../../javascript/reference/getday-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getFullYear-Methode](../../javascript/reference/getfullyear-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getHours-Methode](../../javascript/reference/gethours-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getItem-Methode](../../javascript/reference/getitem-method-vbarray-javascript.md)|J|J|J|J|J|J|J|  
|[getMilliseconds-Methode](../../javascript/reference/getmilliseconds-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getMinutes-Methode](../../javascript/reference/getminutes-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getMonth-Methode](../../javascript/reference/getmonth-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[GetObject-Funktion](../../javascript/reference/getobject-function-javascript.md)|J|J|N|N|N|N|N|  
|[getOwnPropertyDescriptor-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|N|J*|J|J|J|J|J|  
|[getOwnPropertyNames-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md)|N|N|J|J|J|J|J|  
|[getPrototypeOf-Funktion](../../javascript/reference/object-getprototypeof-function-javascript.md)|N|N|J|J|J|J|J|  
|[getSeconds-Methode](../../javascript/reference/getseconds-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getTime-Methode](../../javascript/reference/gettime-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getTimezoneOffset-Methode](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getUTCDate-Methode](../../javascript/reference/getutcdate-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getUTCDay-Methode](../../javascript/reference/getutcday-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getUTCFullYear-Methode](../../javascript/reference/getutcfullyear-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getUTCHours-Methode](../../javascript/reference/getutchours-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getUTCMilliseconds-Methode](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getUTCMinutes-Methode](../../javascript/reference/getutcminutes-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getUTCMonth-Methode](../../javascript/reference/getutcmonth-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getUTCSeconds-Methode](../../javascript/reference/getutcseconds-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[getVarDate-Methode](../../javascript/reference/getvardate-method-date-javascript.md)|J|J|J|J|J|J|N|  
|[getYear-Methode](../../javascript/reference/getyear-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[Global-Objekt](../../javascript/reference/global-object-javascript.md)|J|J|J|J|J|J|J|  
|[global-Eigenschaft](../../javascript/reference/global-property-regular-expression-javascript.md)|J|J|J|J|J|J|J|  
|[Operator Größer als (>)](../../javascript/reference/comparison-operators-javascript.md)|J|J|J|J|J|J|J|  
|[Operator Größer gleich (>=)](../../javascript/reference/comparison-operators-javascript.md)|J|J|J|J|J|J|J|  
|[hasOwnProperty-Methode](../../javascript/reference/hasownproperty-method-object-javascript.md)|J|J|J|J|J|J|J|  
|[HTML-Tag-Methoden](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[hypot-Funktion](../../javascript/reference/math-hypot-function-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[Identity-Operator (===)](../../javascript/reference/comparison-operators-javascript.md)|J|J|J|J|J|J|J|  
|[if...else-Anweisung](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)|J|J|J|J|J|J|J|  
|[ignoreCase-Eigenschaft](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)|J|J|J|J|J|J|J|  
|[imul-Funktion](../../javascript/reference/math-imul-function-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[Operator In](../../javascript/reference/in-operator-decrementjavascript.md)|J|J|J|J|J|J|J|  
|[includes-Methode (String)](../../javascript/reference/includes-method-string-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[Inkrementoperator (++)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|J|J|J|J|J|J|J|  
|[index-Eigenschaft](../../javascript/reference/index-property-regexp-javascript.md)|J|J|J|J|J|J|J|  
|[indexOf-Methode (Array)](../../javascript/reference/indexof-method-array-javascript.md)|N|N|J|J|J|J|J|  
|[indexOf-Methode (String)](../../javascript/reference/indexof-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[Ungleichheitsoperator (!=)](../../javascript/reference/comparison-operators-javascript.md)|J|J|J|J|J|J|J|  
|[Infinity-Konstante](../../javascript/reference/infinity-constant-javascript.md)|J|J|J|J|J|J|J|  
|[input-Eigenschaft ($_)](../../javascript/reference/input-property-dollar-regexp-javascript.md)|J|J|J|J|J|J|J|  
|[instanceof-Operator](../../javascript/reference/instanceof-operator-decrementjavascript.md)|J|J|J|J|J|J|J|  
|[Int8Array-Objekt](../../javascript/reference/int8array-object.md)|N|N|N|J|J|J|J|  
|[Int16Array-Objekt](../../javascript/reference/int16array-object.md)|N|N|N|J|J|J|J|  
|[Int32Array-Objekt](../../javascript/reference/int32array-object.md)|N|N|N|J|J|J|J|  
|[Intl.Collator-Objekt](../../javascript/reference/intl-collator-object-javascript.md)|N|N|N|N|J|J|V8 (Win): N<br />V8.1 (Win): J<br />V8.1 (Phone): J|  
|[Intl.DateTimeFormat-Objekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)|N|N|N|N|J|J|V8: N<br />V8.1: J|  
|[Intl.NumberFormat-Objekt](../../javascript/reference/intl-numberformat-object-javascript.md)|N|N|N|N|J|J|V8: N<br />V8.1: J|  
|[isFinite-Funktion](../../javascript/reference/isfinite-function-javascript.md)|J|J|J|J|J|J|J|  
|[isArray-Funktion](../../javascript/reference/array-isarray-function-javascript.md)|N|N|J|J|J|J|J|  
|[IsExtensible-Funktion](../../javascript/reference/object-isextensible-function-javascript.md)|N|N|J|J|J|J|J|  
|[isFrozen-Funktion](../../javascript/reference/object-isfrozen-function-javascript.md)|N|N|J|J|J|J|J|  
|[IsInteger-Funktion](../../javascript/reference/number-isinteger-function-number-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[isNaN-Funktion](../../javascript/reference/isnan-function-javascript.md)|J|J|J|J|J|J|J|  
|[isNaN-Funktion (Nummer)](../../javascript/reference/number-isnan-function-number-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[ISO-Datumsformat](../../javascript/date-and-time-strings-javascript.md)|N|N|J|J|J|J|J|  
|[IsPrototypeOf-Methode](../../javascript/reference/isprototypeof-method-object-javascript.md)|J|J|J|J|J|J|J|  
|[isSealed-Funktion](../../javascript/reference/object-issealed-function-javascript.md)|N|N|J|J|J|J|J|  
|[italics-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[Iteratoren](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[item-Methode](../../javascript/reference/item-method-enumerator-javascript.md)|J|J|J|J|J|J|J|  
|[join-Methode](../../javascript/reference/join-method-array-javascript.md)|J|J|J|J|J|J|J|  
|[JSON-Objekt](../../javascript/reference/json-object-javascript.md)|N|J|J|J|J|J|J|  
|[keys-Funktion](../../javascript/reference/object-keys-function-javascript.md)|N|N|J|J|J|J|J|  
|[keys-Methode (Array)](../../javascript/reference/keys-method-array-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[Anweisung mit Bezeichnung](../../javascript/reference/labeled-statement-javascript.md)|J|J|J|J|J|J|J|  
|[lastIndex-Eigenschaft](../../javascript/reference/lastindex-property-regexp-javascript.md)|J|J|J|J|J|J|J|  
|[lastIndexOf-Methode (Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|N|N|J|J|J|J|J|  
|[lastIndexOf-Methode (String)](../../javascript/reference/lastindexof-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[lastMatch-Eigenschaft ($&)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)|J|J|J|J|J|J|J|  
|[lastParen-Eigenschaft ($+)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)|J|J|J|J|J|J|J|  
|[lbound-Methode](../../javascript/reference/lbound-method-vbarray-javascript.md)|J|J|J|J|J|J|J|  
|[leftContext-Eigenschaft ($')](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)|J|J|J|J|J|J|J|  
|[Left Shift-Zuweisungsoperator (<<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)|J|J|J|J|J|J|J|  
|[length-Eigenschaft (Arguments)](../../javascript/reference/length-property-arguments-javascript.md)|J|J|J|J|J|J|J|  
|[length-Eigenschaft (Array)](../../javascript/reference/length-property-array-javascript.md)|J|J|J|J|J|J|J|  
|[length-Eigenschaft (Funktion)](../../javascript/reference/length-property-function-javascript.md)|J|J|J|J|J|J|J|  
|[length-Eigenschaft (String)](../../javascript/reference/length-property-string-javascript.md)|J|J|J|J|J|J|J|  
|[Operator Kleiner als (<)](../../javascript/reference/comparison-operators-javascript.md)|J|J|J|J|J|J|J|  
|[Operator Kleiner gleich (<=)](../../javascript/reference/comparison-operators-javascript.md)|J|J|J|J|J|J|J|  
|[let-Anweisung](../../javascript/reference/let-statement-javascript.md)|N|N|N|N|J|J|V8: N<br />V8.1: J|  
|[link-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[LN2-Konstante](../../javascript/reference/math-constants-javascript.md)|J|J|J|J|J|J|J|  
|[LN10-Konstante](../../javascript/reference/math-constants-javascript.md)|J|J|J|J|J|J|J|  
|[localeCompare-Methode](../../javascript/reference/localecompare-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[log-Funktion](../../javascript/reference/math-log-function-javascript.md)|J|J|J|J|J|J|J|  
|[LOG2E-Konstante](../../javascript/reference/math-constants-javascript.md)|J|J|J|J|J|J|J|  
|[LOG10E-Konstante](../../javascript/reference/math-constants-javascript.md)|J|J|J|J|J|J|J|  
|[Logischer AND-Operator (&&)](../../javascript/reference/logical-and-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[Logischer NOT-Operator (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|J|J|J|J|J|J|J|  
|[Logisches OR-Operator (&#124; &#124;)](../../javascript/reference/logical-or-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[map-Methode](../../javascript/reference/map-method-array-javascript.md)|N|N|J|J|J|J|J|  
|[Map-Objekt](../../javascript/reference/map-object-javascript.md)|N|N|N|N|J|J|V8: N<br />V8.1: J|  
|[match-Methode](../../javascript/reference/match-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[Math-Objekt](../../javascript/reference/math-object-javascript.md)|J|J|J|J|J|J|J|  
|[max-Funktion](../../javascript/reference/math-max-function-javascript.md)|J|J|J|J|J|J|J|  
|[MAX_VALUE-Konstante](../../javascript/reference/number-constants-javascript.md)|J|J|J|J|J|J|J|  
|[message-Eigenschaft](../../javascript/reference/message-property-error-javascript.md)|J|J|J|J|J|J|J|  
|[min-Funktion](../../javascript/reference/math-min-function-javascript.md)|J|J|J|J|J|J|J|  
|[MIN_VALUE-Konstante](../../javascript/reference/number-constants-javascript.md)|J|J|J|J|J|J|J|  
|[Rest-Zuweisungsoperator (% =)](../../javascript/reference/modulus-assignment-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[Restoperator (%)](../../javascript/reference/modulus-operator-decrementjavascript.md)|J|J|J|J|J|J|J|  
|[moveFirst-Methode](../../javascript/reference/movefirst-method-enumerator-javascript.md)|J|J|J|J|J|J|J|  
|[moveNext-Methode](../../javascript/reference/movenext-method-enumerator-javascript.md)|J|J|J|J|J|J|J|  
|[multiline-Eigenschaft](../../javascript/reference/multiline-property-regular-expression-javascript.md)|J|J|J|J|J|J|J|  
|[Multiplikationszuweisungsoperator (*=)](../../javascript/reference/multiplication-assignment-operator-decrement-equal-javascript.md)|J|J|J|J|J|J|J|  
|[Multiplikationsoperator (*)](../../javascript/reference/multiplication-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[name-Eigenschaft](../../javascript/reference/name-property-error-javascript.md)|J|J|J|J|J|J|J|  
|[NaN-Konstante (Global)](../../javascript/reference/nan-constant-javascript.md)|J|J|J|J|J|J|J|  
|[NaN-Konstante (Number)](../../javascript/reference/number-constants-javascript.md)|J|J|J|J|J|J|J|  
|[NEGATIVE_INFINITY-Konstante](../../javascript/reference/number-constants-javascript.md)|J|J|J|J|J|J|J|  
|[new-Operator](../../javascript/reference/new-operator-decrementjavascript.md)|J|J|J|J|J|J|J|  
|[Nichtidentitätsoperator (!==)](../../javascript/reference/comparison-operators-javascript.md)|J|J|J|J|J|J|J|  
|[now-Funktion](../../javascript/reference/date-now-function-javascript.md)|N|N|J|J|J|J|J|  
|[Number-Objekt](../../javascript/reference/number-object-javascript.md)|J|J|J|J|J|J|J|  
|[number-Eigenschaft](../../javascript/reference/number-property-error-javascript.md)|J|J|J|J|J|J|J|  
|[Object-Objekt](../../javascript/reference/object-object-javascript.md)|J|J|J|J|J|J|J|  
|[Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)|J|J|J|J|J|J|J|  
|[Date.parse-Funktion](../../javascript/reference/date-parse-function-javascript.md)|J|J|J|J|J|J|J|  
|[JSON.parse-Funktion](../../javascript/reference/json-parse-function-javascript.md)|N|J|J|J|J|J|J|  
|[parseFloat-Funktion](../../javascript/reference/parsefloat-function-javascript.md)|J|J|J|J|J|J|J|  
|[parseInt-Funktion](../../javascript/reference/parseint-function-javascript.md)|J|J|J|J|J|J|J|  
|[PI-Konstante](../../javascript/reference/math-constants-javascript.md)|J|J|J|J|J|J|J|  
|[pop-Methode](../../javascript/reference/pop-method-array-javascript.md)|J|J|J|J|J|J|J|  
|[POSITIVE_INFINITY-Konstante](../../javascript/reference/number-constants-javascript.md)|J|J|J|J|J|J|J|  
|[pow-Funktion](../../javascript/reference/math-pow-function-javascript.md)|J|J|J|J|J|J|J|  
|[preventExtensions-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md)|N|N|J|J|J|J|J|  
|[Promise-Objekt](../../javascript/reference/promise-object-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[prototype-Eigenschaft](../../javascript/reference/prototype-property-object-javascript.md)|J|J|J|J|J|J|J|  
|[propertyIsEnumerable-Methode](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|J|J|J|J|J|J|J|  
|[Proxy-Objekt](../../javascript/reference/proxy-object-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[push-Methode](../../javascript/reference/push-method-array-javascript.md)|J|J|J|J|J|J|J|  
|[random-Funktion](../../javascript/reference/math-random-function-javascript.md)|J|J|J|J|J|J|J|  
|[raw-Funktion](../../javascript/reference/string-raw-function-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[reduce-Methode](../../javascript/reference/reduce-method-array-javascript.md)|N|N|J|J|J|J|J|  
|[reduceRight-Methode](../../javascript/reference/reduceright-method-array-javascript.md)|N|N|J|J|J|J|J|  
|[RegExp-Objekt](../../javascript/reference/regexp-object-javascript.md)|J|J|J|J|J|J|J|  
|[Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)|J|J|J|J|J|J|J|  
|[Syntax regulärer Ausdrücke](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)|J|J|J|J|J|J|J|  
|[Regulärausdruck/y-Flag](../../javascript/reference/regular-expression-object-javascript.md)|N|N|N|N|N|Exp.|V8.1: N<br />V10: Exp.|  
|[repeat-Methode (String)](../../javascript/reference/repeat-method-string-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[replace-Methode](../../javascript/reference/replace-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[Funktionen](../../javascript/functions-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[return-Anweisung](../../javascript/reference/return-statement-javascript.md)|J|J|J|J|J|J|J|  
|[reverse-Methode](../../javascript/reference/reverse-method-javascript.md)|J|J|J|J|J|J|J|  
|[rightContext-Eigenschaft ($')](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)|J|J|J|J|J|J|J|  
|[Right Shift-Zuweisungsoperator (>>=)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)|J|J|J|J|J|J|J|  
|[round-Funktion](../../javascript/reference/math-round-function-javascript.md)|J|J|J|J|J|J|J|  
|[ScriptEngine-Funktion](../../javascript/reference/scriptengine-function-javascript.md)|J|J|J|J|J|J|J|  
|[ScriptEngineBuildVersion-Funktion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)|J|J|J|J|J|J|J|  
|[ScriptEngineMajorVersion-Funktion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)|J|J|J|J|J|J|J|  
|[ScriptEngineMinorVersion-Funktion](../../javascript/reference/scriptengineminorversion-function-javascript.md)|J|J|J|J|J|J|J|  
|[seal-Funktion](../../javascript/reference/object-seal-function-javascript.md)|N|N|J|J|J|J|J|  
|[search-Methode](../../javascript/reference/search-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[Set-Objekt](../../javascript/reference/set-object-javascript.md)|N|N|N|N|J|J|V8: N<br />V8.1: J|  
|[setDate-Methode](../../javascript/reference/setdate-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setFullYear-Methode](../../javascript/reference/setfullyear-method-date-javascript.md)||J|J|J|J|J|J|  
|[setHours-Methode](../../javascript/reference/sethours-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setMilliseconds-Methode](../../javascript/reference/setmilliseconds-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setMinutes-Methode](../../javascript/reference/setminutes-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setMonth-Methode](../../javascript/reference/setmonth-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setSeconds-Methode](../../javascript/reference/setseconds-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setTime-Methode](../../javascript/reference/settime-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setUTCDate-Methode](../../javascript/reference/setutcdate-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setUTCFullYear-Methode](../../javascript/reference/setutcfullyear-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setUTCHours-Methode](../../javascript/reference/setutchours-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setUTCMilliseconds-Methode](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setUTCMinutes-Methode](../../javascript/reference/setutcminutes-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setUTCMonth-Methode](../../javascript/reference/setutcmonth-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setUTCSeconds-Methode](../../javascript/reference/setutcseconds-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[setYear-Methode](../../javascript/reference/setyear-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[shift-Methode](../../javascript/reference/shift-method-array-javascript.md)|J|J|J|J|J|J|J|  
|[sin-Funktion](../../javascript/reference/math-sin-function-javascript.md)|J|J|J|J|J|J|J|  
|[slice-Methode (Array)](../../javascript/reference/slice-method-array-javascript.md)|J|J|J|J|J|J|J|  
|[slice-Methode (String)](../../javascript/reference/slice-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[small-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[some-Methode](../../javascript/reference/some-method-array-javascript.md)|N|N|J|J|J|J|J|  
|[sort-Methode](../../javascript/reference/sort-method-array-javascript.md)|J|J|J|J|J|J|J|  
|[source-Eigenschaft](../../javascript/reference/source-property-regular-expression-javascript.md)|J|J|J|J|J|J|J|  
|[splice-Methode](../../javascript/reference/splice-method-array-javascript.md)|J|J|J|J|J|J|J|  
|[split-Methode](../../javascript/reference/split-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[Funktionen](../../javascript/functions-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[sqrt-Funktion](../../javascript/reference/math-sqrt-function-javascript.md)|J|J|J|J|J|J|J|  
|[SQRT1_2-Konstante](../../javascript/reference/math-constants-javascript.md)|J|J|J|J|J|J|J|  
|[SQRT2-Konstante](../../javascript/reference/math-constants-javascript.md)|J|J|J|J|J|J|J|  
|[use strict-Direktive](../../javascript/reference/use-strict-directive.md)|N|N|N|J|J|J|J|  
|[strike-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[String-Objekt](../../javascript/reference/string-object-javascript.md)|J|J|J|J|J|J|J|  
|[JSON.stringify-Funktion](../../javascript/reference/json-stringify-function-javascript.md)|N|J|J|J|J|J|J|  
|[sub-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[substr-Methode](../../javascript/reference/substr-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[substring-Methode](../../javascript/reference/substring-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[Subtraktionszuweisungsoperator (-=)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)|J|J|J|J|J|J|J|  
|[Subtraktionsoperator (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[sup-Methode](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|J|  
|[switch-Anweisung](../../javascript/reference/switch-statement-javascript.md)|J|J|J|J|J|J|J|  
|[Symbol-Objekt](../../javascript/reference/symbol-object-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[tan-Funktion](../../javascript/reference/math-tan-function-javascript.md)|J|J|J|J|J|J|J|  
|[Vorlagenzeichenfolgen](../../javascript/advanced/template-strings-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[test-Methode](../../javascript/reference/test-method-regular-expression-javascript.md)|J|J|J|J|J|J|J|  
|[this-Anweisung](../../javascript/reference/this-statement-javascript.md)|J|J|J|J|J|J|J|  
|[throw-Anweisung](../../javascript/reference/throw-statement-javascript.md)|J|J|J|J|J|J|J|  
|[toArray-Methode](../../javascript/reference/toarray-method-vbarray-javascript.md)|J|J|J|J|J|J|J|  
|[toDateString-Methode](../../javascript/reference/todatestring-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[toExponential-Methode](../../javascript/reference/toexponential-method-number-javascript.md)|J|J|J|J|J|J|J|  
|[toFixed-Methode](../../javascript/reference/tofixed-method-number-javascript.md)|J|J|J|J|J|J|J|  
|[toGMTString-Methode](../../javascript/reference/togmtstring-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[toISOString-Methode](../../javascript/reference/toisostring-method-date-javascript.md)|N|N|J|J|J|J|J|  
|[toJSON-Methode](../../javascript/reference/tojson-method-date-javascript.md)|N|J|J|J|J|J|J|  
|[toLocaleDateString-Methode](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[toLocaleLowercase-Methode](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[toLocaleString-Methode](../../javascript/reference/tolocalestring-method-object-javascript.md)|J|J|J|J|J|J|J|  
|[toLocaleTimeString-Methode](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[toLocaleUppercase-Methode](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[toLowerCase-Methode](../../javascript/reference/tolowercase-method-javascript.md)|J|J|J|J|J|J|J|  
|[toPrecision-Methode](../../javascript/reference/toprecision-method-number-javascript.md)|J|J|J|J|J|J|J|  
|[toString-Methode](../../javascript/reference/tostring-method-object-javascript.md)|J|J|J|J|J|J|J|  
|[toTimeString-Methode](../../javascript/reference/totimestring-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[toUpperCase-Methode](../../javascript/reference/touppercase-method-string-javascript.md)|J|J|J|J|J|J|J|  
|[toUTCString-Methode](../../javascript/reference/toutcstring-method-date-javascript.md)|J|J|J|J|J|J|J|  
|[trim-Methode](../../javascript/reference/trim-method-string-javascript.md)|N|N|J|J|J|J|J|  
|[try-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|J|J|J|J|J|J|J|  
|[typeof-Operator](../../javascript/reference/typeof-operator-decrementjavascript.md)|J|J|J|J|J|J|J|  
|[ubound-Methode](../../javascript/reference/ubound-method-vbarray-javascript.md)|J|J|J|J|J|J|J|  
|[Uint8Array-Objekt](../../javascript/reference/uint8array-object.md)|N|N|N|J|J|J|J|  
|[Uint16Array-Objekt](../../javascript/reference/uint16array-object.md)|N|N|N|J|J|J|J|  
|[Uint32Array-Objekt](../../javascript/reference/uint32array-object.md)|N|N|N|J|J|J|J|  
|[Uint8ClampedArray-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)|N|N|N|N|J|J|V8: Nein<br />V8.1 (Win): Ja<br />V8.1 (Phone): Nein<br />V10: J|  
|[Unärer Negationsoperator (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[undefined-Konstante](../../javascript/reference/undefined-constant-javascript.md)|J|J|J|J|J|J|J|  
|[unescape-Funktion](../../javascript/reference/unescape-function-javascript.md)|J|J|J|J|J|J|J|  
|[Unicode-Codepunkt-Escape-Zeichen](../../javascript/advanced/special-characters-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[unshift-Methode](../../javascript/reference/unshift-method-array-javascript.md)|J|J|J|J|J|J|J|  
|[Vorzeichenloser Right Shift-Zuweisungsoperator (>>>=)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)|J|J|J|J|J|J|J|  
|[Vorzeichenloser Right Shift-Operator (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|J|J|J|J|J|J|J|  
|[use strict-Direktive](../../javascript/reference/use-strict-directive.md)|N|N|N|J|J|J|J|  
|[UTC-Funktion](../../javascript/reference/date-utc-function-javascript.md)|J|J|J|J|J|J|J|  
|[valueOf-Methode](../../javascript/reference/valueof-method-object-javascript.md)|J|J|J|J|J|J|J|  
|[values-Methode (Array)](../../javascript/reference/values-method-array-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[var-Anweisung](../../javascript/reference/var-statement-javascript.md)|J|J|J|J|J|J|J|  
|[VBArray-Objekt](../../javascript/reference/vbarray-object-javascript.md)|J|J|J|J|J|J|N|  
|[void-Operator](../../javascript/reference/void-operator-decrementjavascript.md)|J|J|J|J|J|J|J|  
|[WeakMap-Objekt](../../javascript/reference/weakmap-object-javascript.md)|N|N|N|N|J|J|V8: N<br />V8.1: J|  
|[WeakSet-Objekt](../../javascript/reference/weakset-object-javascript.md)|N|N|N|N|N|J|V8.1: N<br />V10: J|  
|[while-Anweisung](../../javascript/reference/while-statement-javascript.md)|J|J|J|J|J|J|J|  
|[WinRTError-Objekt](../../javascript/reference/winrterror-object-javascript.md)|N|N|N|J|J|J|J|  
|[with-Anweisung](../../javascript/reference/with-statement-javascript.md)|J|J|J|J|J|J|J|  
|[write-Funktion](../../javascript/reference/debug-write-function-javascript.md)|J|J|J|J|J|J|J|  
|[writeln-Funktion](../../javascript/reference/debug-writeln-function-javascript.md)|J|J|J|J|J|J|J|  
  
 \* Unterstützt DOM-Objekte, jedoch keine benutzerdefinierten Objekte. Die Attribute `enumerable` und `configurable` können angegeben werden, werden jedoch nicht verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren der Dokumentkompatibilität](http://go.microsoft.com/fwlink/?LinkId=208537)
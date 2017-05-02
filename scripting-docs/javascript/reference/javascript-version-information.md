---
title: "JavaScript-Versionsinformationen | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, Versionsinformationen"
ms.assetid: 440f4924-f7a9-48e0-873e-bd599a93b437
caps.latest.revision: 93
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 93
---
# JavaScript-Versionsinformationen
Unterschiedliche Versionen von JavaScript unterstützen unterschiedliche Sätze von JavaScript\-Elementen.[!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-Apps unterstützen einen etwas anderen Satz von Funktionen als Internet Explorer.  
  
> [!IMPORTANT]
>  Eine [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-App ist eine neue Anwendungsart, die auf [!INCLUDE[win8](../../includes/win8-md.md)]\-Geräten ausgeführt wird. Mehr über [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-Apps finden Sie unter [What's a Windows Store app?](http://msdn.microsoft.com/de-de/231c1fba-9f87-468e-94aa-45dd57edcc70)  
  
 Der Standardmodus \(der bis zu Internet Explorer 11 in allen Versionen von Internet Explorer verwendete Modus, sofern die `<!doctype>`\-Direktive vorhanden ist\) unterstützt einen anderen Elementsatz als der Quirksmodus \(der Modus, der verwendet wird, wenn keine `<!doctype>`\-Direktive vorhanden ist\). Weitere Informationen zur Versionsverwaltung finden Sie unter [Definieren der Dokumentkompatibilität](http://go.microsoft.com/fwlink/?LinkId=208537).  
  
 In der folgenden Tabelle werden die Dokumentmodi in Internet Explorer \(und Store\-Apps, die [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] und [!INCLUDE[winphone_appname](../../includes/winphone-appname-md.md)] darstellen\) angezeigt, die bestimmte Sprachelemente unterstützen. Dokumentmodi, die ein bestimmtes Element unterstützen, werden mit dem Buchstaben **J** angezeigt. Dokumentmodi, die kein bestimmtes Element unterstützen, werden mit dem Buchstaben **N** angezeigt.  
  
> [!IMPORTANT]
>  [!INCLUDE[jsv12text](../../includes/jsv12text-md.md)] \(Edge\-Browser in Windows 10\) bietet keine Unterstützung für ältere Dokumentmodi. Unterstützung von [!INCLUDE[winphone_appname](../../includes/winphone-appname-md.md)]\-Apps beginnt mit Windows Phone 8.1. Experimentelle Features \(about:flags\) sind mit „Exp.“ gekennzeichnet.  
  
 Die Tabelle enthält zusammenfassende Informationen. Genauere Informationen finden Sie in der Dokumentation für das Sprachelement  
  
|Sprachelement|Quirks, Internet Explorer 6\-Standards und Internet Explorer 7\-Standards|Internet Explorer 8\-Standards|Internet Explorer 9\-Standards|Internet Explorer 10\-Standards|Internet Explorer 11\-Standards|Rand|Store\-Apps|  
|-------------------|-------------------------------------------------------------------------------|------------------------------------|------------------------------------|-------------------------------------|-------------------------------------|----------|-----------------|  
|[\_\_proto\_\_\-Eigenschaft \(Object\)](../../javascript/reference/proto-property-object-javascript.md)|N|N|N|N|J|Y|V8 \(Win\): N<br />V8.1 \(Win\): J<br />V8.1 \(Phone\): J|  
|[$1...$9\-Eigenschaften \(RegExp\)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)|Y|J|J|J|J|J|Y|  
|[0n\-Eigenschaft](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)|Y|J|J|J|J|J|Y|  
|[abs\-Funktion](../../javascript/reference/math-abs-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[acos\-Funktion](../../javascript/reference/math-acos-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[acosh\-Funktion](../../javascript/reference/math-acosh-function-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[ActiveXObject\-Objekt](../../javascript/reference/activexobject-object-javascript.md)|Y|J|J|J|J|J|N|  
|[Additionszuweisungsoperator \(\+\=\)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[Additionsoperator \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[apply\-Methode](../../javascript/reference/apply-method-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[arguments\-Objekt](../../javascript/reference/arguments-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[arguments\-Eigenschaft](../../javascript/reference/arguments-property-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[Array\-Objekt](../../javascript/reference/array-object-javascript.md)|Y|J|J|J|J|J|J|  
|[Array.from\-Funktion \(Array\)](../../javascript/reference/array-from-function-array-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[Array.isArray\-Funktion](../../javascript/reference/array-isarray-function-javascript.md)|N|N|J|J|J|J|J|  
|[Array.of\-Funktion \(Array\)](../../javascript/reference/array-of-function-array-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md)|N|N|N|J|J|J|J|  
|[Funktionen](../../javascript/functions-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[asin\-Funktion](../../javascript/reference/math-asin-function-javascript.md)|Y|J|J|J|J|J|J|  
|[Object.assign\-Funktion \(Objekt\)](../../javascript/reference/object-assign-function-object-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[Zuweisungsoperator \(\=\)](../../javascript/reference/assignment-operator-decrement-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[atan\-Funktion](../../javascript/reference/math-atan-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[atan2\-Funktion](../../javascript/reference/math-atan2-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[atEnd\-Methode](../../javascript/reference/atend-method-enumerator-javascript.md)|Y|J|J|J|J|J|N|  
|[bind\-Methode](../../javascript/reference/bind-method-function-javascript.md)|N|N|J|J|J|J|Y|  
|[Bitweiser AND\-Zuweisungsoperator \(&\=\)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[Bitweiser AND\-Operator \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[Bitweiser Left Shift\-Operator \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[Bitweiser NOT\-Operator \(~\)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|Y|J|J|J|J|J|Y|  
|[Bitweiser OR\-Zuweisungsoperator \(&#124;\=\)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[Bitweiser OR\-Operator \(&#124;\)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[Bitweiser Right\-Shift\-Operator \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[Bitweiser YOR‑Zuweisungsoperator \(^\=\)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[Bitweiser YOR‑Operator \(^\)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|Y|J|J|J|J|J|Y|  
|[blink\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|Y|  
|[bold\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|Y|  
|[Boolean\-Objekt](../../javascript/reference/boolean-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[break\-Anweisung](../../javascript/reference/break-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[call\-Methode](../../javascript/reference/call-method-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[callee\-Eigenschaft](../../javascript/reference/callee-property-arguments-javascript.md)|Y|J|J|J|J|J|Y|  
|[caller\-Eigenschaft](../../javascript/reference/caller-property-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[catch\-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[ceil\-Funktion](../../javascript/reference/math-ceil-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[charAt\-Methode](../../javascript/reference/charat-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[charCodeAt\-Methode](../../javascript/reference/charcodeat-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[class\-Anweisung](../../javascript/reference/class-statement-javascript.md)|N|N|N|N|N|Exp.|V8.1: N<br />V10: Exp.|  
|[codePointAt\-Methode \(String\)](../../javascript/reference/codepointat-method-string-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[Kommaoperator \(,\)](../../javascript/reference/comma-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[\/\/ \(Einzeilige Kommentaranweisung\)](../../javascript/reference/comment-statements-javascript.md)|Y|J|J|J|J|J|Y|  
|[\/\*..\*\/ \(Mehrzeilige Kommentaranweisung\)](../../javascript/reference/comment-statements-javascript.md)|Y|J|J|J|J|J|Y|  
|[Vergleichsoperatoren](../../javascript/reference/comparison-operators-javascript.md)|Y|J|J|J|J|J|Y|  
|[compile\-Methode](../../javascript/reference/compile-method-regular-expression-javascript.md)|Y|J|J|J|J|J|Y|  
|[concat\-Methode \(Array\)](../../javascript/reference/concat-method-array-javascript.md)|Y|J|J|J|J|J|Y|  
|[concat\-Methode \(String\)](../../javascript/reference/concat-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)|Y|J|J|J|N|N|N|  
|[Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)|Y|J|J|J|N|N|N|  
|[Bedingter \(ternärer\) Operator \(?:\)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[constructor\-Eigenschaft](../../javascript/reference/constructor-property-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[const\-Anweisung](../../javascript/reference/const-statement-javascript.md)|N|N|N|N|J|Y|V8 \(Win\): N<br />V8.1 \(Win\): J<br />V8.1 \(Phone\): J|  
|[continue\-Anweisung](../../javascript/reference/continue-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[cos\-Funktion](../../javascript/reference/math-cos-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[create\-Funktion](../../javascript/reference/object-create-function-javascript.md)|N|N|J|J|J|J|J|  
|[DataView\-Objekt](../../javascript/reference/dataview-object.md)|N|N|N|J|J|J|Y|  
|[Date\-Objekt](../../javascript/reference/date-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[Debugobjekt](../../javascript/reference/debug-object-javascript.md)|Y|J|J|J|J|J|J|  
|[Debug.setNonUserCodeExceptions\-Eigenschaft](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|J|J|J|J|  
|[Debug.setNonUserCodeExceptions\-Eigenschaft](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|J|J|J|Y|  
|[debugger\-Anweisung](../../javascript/reference/debugger-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[decodeURI\-Funktion](../../javascript/reference/decodeuri-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[DecodeURIComponent\-Funktion](../../javascript/reference/decodeuricomponent-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[Dekrementoperator \(\-\-\)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|J|J|J|J|J|J|  
|[Funktionen](../../javascript/functions-javascript.md)|N|N|N|N|N|Exp.|V8.1: N<br />V10: Exp.|  
|[defineProperties\-Funktion](../../javascript/reference/object-defineproperties-function-javascript.md)|N|J\*|J|J|J|J|Y|  
|[defineProperty\-Funktion](../../javascript/reference/object-defineproperty-function-javascript.md)|N|J\*|J|J|J|J|Y|  
|[delete\-Operator](../../javascript/reference/delete-operator-decrementjavascript.md)|Y|J|J|J|J|J|Y|  
|[description\-Eigenschaft](../../javascript/reference/description-property-error-javascript.md)|Y|J|J|J|J|J|Y|  
|[dimensions\-Methode](../../javascript/reference/dimensions-method-vbarray-javascript.md)|Y|J|J|J|J|J|Y|  
|[Divisionszuweisungsoperator \(\/\=\)](../../javascript/reference/division-assignment-operator-decrement-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[Divisionsoperator \(\/\)](../../javascript/reference/division-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[do...while\-Anweisung](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[E\-Konstante](../../javascript/reference/math-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[encodeURI\-Funktion](../../javascript/reference/encodeuri-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[encodeURI\-Komponentenfunktion](../../javascript/reference/encodeuricomponent-function-javascript.md)|Y|J|J|J|J|J|J|  
|[entries\-Methode \(Array\)](../../javascript/reference/entries-method-array-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[Enumeratorobjekt](../../javascript/reference/enumerator-object-javascript.md)|Y|J|J|J|J|J|N|  
|[Nummerkonstanten](../../javascript/reference/number-constants-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[Gleichheitsoperator \(\=\=\)](../../javascript/reference/comparison-operators-javascript.md)|Y|J|J|J|J|J|Y|  
|[Error\-Objekt](../../javascript/reference/error-object-javascript.md)|Y|J|J|J|J|J|J|  
|[stack\-Eigenschaft \(Fehler\)](../../javascript/reference/stack-property-error-javascript.md)|N|N|N|J|J|J|J|  
|[stackTraceLimit\-Eigenschaft \(Fehler\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)|N|N|N|J|J|J|Y|  
|[escape\-Funktion](../../javascript/reference/escape-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[eval\-Funktion](../../javascript/reference/eval-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[exec\-Methode](../../javascript/reference/exec-method-regular-expression-javascript.md)|Y|J|J|J|J|J|Y|  
|[every\-Methode](../../javascript/reference/every-method-array-javascript.md)|N|N|J|J|J|J|Y|  
|[exp\-Funktion](../../javascript/reference/math-exp-function-javascript.md)|Y|J|J|J|J|J|J|  
|[fill\-Methode \(Array\)](../../javascript/reference/fill-method-array-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[filter\-Methode](../../javascript/reference/filter-method-array-javascript.md)|N|N|J|J|J|J|Y|  
|[finally\-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|J|J|J|J|J|J|  
|[findIndex\-Methode \(Array\)](../../javascript/reference/findindex-method-array-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[fixed\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|J|  
|[Float32Array\-Objekt](../../javascript/reference/float32array-object.md)|N|N|N|J|J|J|J|  
|[Float64Array\-Objekt](../../javascript/reference/float64array-object.md)|N|N|N|J|J|J|Y|  
|[floor\-Funktion](../../javascript/reference/math-floor-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[fontcolor\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|Y|  
|[fontsize\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|Y|  
|[for\-Anweisung](../../javascript/reference/for-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[forEach\-Methode](../../javascript/reference/foreach-method-array-javascript.md)|N|N|J|J|J|J|Y|  
|[for...in\-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[for…of\-Anweisung](../../javascript/reference/for-dot-dot-dot-of-statement-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[freeze\-Funktion](../../javascript/reference/object-freeze-function-javascript.md)|N|N|J|J|J|J|Y|  
|[fromCharCode\-Funktion](../../javascript/reference/string-fromcharcode-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[fromCodePoint\-Funktion](../../javascript/reference/string-fromcodepoint-function-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[Function\-Objekt](../../javascript/reference/function-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[function\-Anweisung](../../javascript/reference/function-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[Generatoren](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Exp.|V8.1: N<br />V10: Exp.|  
|[getDate\-Methode](../../javascript/reference/getdate-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getDay\-Methode](../../javascript/reference/getday-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getFullYear\-Methode](../../javascript/reference/getfullyear-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getHours\-Methode](../../javascript/reference/gethours-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getItem\-Methode](../../javascript/reference/getitem-method-vbarray-javascript.md)|Y|J|J|J|J|J|Y|  
|[getMilliseconds\-Methode](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getMinutes\-Methode](../../javascript/reference/getminutes-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getMonth\-Methode](../../javascript/reference/getmonth-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[GetObject\-Funktion](../../javascript/reference/getobject-function-javascript.md)|Y|J|N|N|N|N|N|  
|[getOwnPropertyDescriptor\-Funktion](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|N|J\*|J|J|J|J|Y|  
|[getOwnPropertyNames\-Funktion](../../javascript/reference/object-getownpropertynames-function-javascript.md)|N|N|J|J|J|J|Y|  
|[getPrototypeOf\-Funktion](../../javascript/reference/object-getprototypeof-function-javascript.md)|N|N|J|J|J|J|Y|  
|[getSeconds\-Methode](../../javascript/reference/getseconds-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getTime\-Methode](../../javascript/reference/gettime-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getTimezoneOffset\-Methode](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getUTCDate\-Methode](../../javascript/reference/getutcdate-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getUTCDay\-Methode](../../javascript/reference/getutcday-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getUTCFullYear\-Methode](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getUTCHours\-Methode](../../javascript/reference/getutchours-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getUTCMilliseconds\-Methode](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getUTCMinutes\-Methode](../../javascript/reference/getutcminutes-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getUTCMonth\-Methode](../../javascript/reference/getutcmonth-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getUTCSeconds\-Methode](../../javascript/reference/getutcseconds-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[getVarDate\-Methode](../../javascript/reference/getvardate-method-date-javascript.md)|Y|J|J|J|J|J|N|  
|[getYear\-Methode](../../javascript/reference/getyear-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[Global\-Objekt](../../javascript/reference/global-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[global\-Eigenschaft](../../javascript/reference/global-property-regular-expression-javascript.md)|Y|J|J|J|J|J|Y|  
|[Operator Größer als \(\>\)](../../javascript/reference/comparison-operators-javascript.md)|Y|J|J|J|J|J|Y|  
|[Operator Größer gleich \(\>\=\)](../../javascript/reference/comparison-operators-javascript.md)|Y|J|J|J|J|J|Y|  
|[hasOwnProperty\-Methode](../../javascript/reference/hasownproperty-method-object-javascript.md)|Y|J|J|J|J|J|J|  
|[HTML\-Tag\-Methoden](../../javascript/reference/html-tag-methods-javascript.md)|J|J|J|J|J|J|Y|  
|[hypot\-Funktion](../../javascript/reference/math-hypot-function-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[Identity\-Operator \(\=\=\=\)](../../javascript/reference/comparison-operators-javascript.md)|Y|J|J|J|J|J|Y|  
|[if...else\-Anweisung](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[ignoreCase\-Eigenschaft](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)|Y|J|J|J|J|J|Y|  
|[imul\-Funktion](../../javascript/reference/math-imul-function-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[Operator In](../../javascript/reference/in-operator-decrementjavascript.md)|Y|J|J|J|J|J|Y|  
|[includes\-Methode \(String\)](../../javascript/reference/includes-method-string-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[Inkrementoperator \(\+\+\)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|Y|J|J|J|J|J|Y|  
|[index\-Eigenschaft](../../javascript/reference/index-property-regexp-javascript.md)|Y|J|J|J|J|J|Y|  
|[indexOf\-Methode \(Array\)](../../javascript/reference/indexof-method-array-javascript.md)|N|N|J|J|J|J|Y|  
|[indexOf\-Methode \(String\)](../../javascript/reference/indexof-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[Ungleichheitsoperator \(\!\=\)](../../javascript/reference/comparison-operators-javascript.md)|Y|J|J|J|J|J|Y|  
|[Infinity\-Konstante](../../javascript/reference/infinity-constant-javascript.md)|Y|J|J|J|J|J|Y|  
|[input\-Eigenschaft \($\_\)](../../javascript/reference/input-property-dollar-regexp-javascript.md)|Y|J|J|J|J|J|Y|  
|[instanceof\-Operator](../../javascript/reference/instanceof-operator-decrementjavascript.md)|Y|J|J|J|J|J|J|  
|[Int8Array\-Objekt](../../javascript/reference/int8array-object.md)|N|N|N|J|J|J|J|  
|[Int16Array\-Objekt](../../javascript/reference/int16array-object.md)|N|N|N|J|J|J|J|  
|[Int32Array\-Objekt](../../javascript/reference/int32array-object.md)|N|N|N|J|J|J|J|  
|[Intl.Collator\-Objekt](../../javascript/reference/intl-collator-object-javascript.md)|N|N|N|N|J|Y|V8 \(Win\): N<br />V8.1 \(Win\): J<br />V8.1 \(Phone\): J|  
|[Intl.DateTimeFormat\-Objekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)|N|N|N|N|J|Y|V8: N<br />V8.1: J|  
|[Intl.NumberFormat\-Objekt](../../javascript/reference/intl-numberformat-object-javascript.md)|N|N|N|N|J|Y|V8: N<br />V8.1: J|  
|[isFinite\-Funktion](../../javascript/reference/isfinite-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[isArray\-Funktion](../../javascript/reference/array-isarray-function-javascript.md)|N|N|J|J|J|J|Y|  
|[IsExtensible\-Funktion](../../javascript/reference/object-isextensible-function-javascript.md)|N|N|J|J|J|J|Y|  
|[isFrozen\-Funktion](../../javascript/reference/object-isfrozen-function-javascript.md)|N|N|J|J|J|J|Y|  
|[IsInteger\-Funktion](../../javascript/reference/number-isinteger-function-number-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[isNaN\-Funktion](../../javascript/reference/isnan-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[isNaN\-Funktion \(Nummer\)](../../javascript/reference/number-isnan-function-number-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[ISO\-Datumsformat](../../javascript/date-and-time-strings-javascript.md)|N|N|J|J|J|J|Y|  
|[IsPrototypeOf\-Methode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[isSealed\-Funktion](../../javascript/reference/object-issealed-function-javascript.md)|N|N|J|J|J|J|Y|  
|[italics\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|Y|  
|[Iteratoren](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[item\-Methode](../../javascript/reference/item-method-enumerator-javascript.md)|Y|J|J|J|J|J|Y|  
|[join\-Methode](../../javascript/reference/join-method-array-javascript.md)|Y|J|J|J|J|J|Y|  
|[JSON\-Objekt](../../javascript/reference/json-object-javascript.md)|N|J|J|J|J|J|Y|  
|[keys\-Funktion](../../javascript/reference/object-keys-function-javascript.md)|N|N|J|J|J|J|J|  
|[keys\-Methode \(Array\)](../../javascript/reference/keys-method-array-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[Anweisung mit Bezeichnung](../../javascript/reference/labeled-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[lastIndex\-Eigenschaft](../../javascript/reference/lastindex-property-regexp-javascript.md)|Y|J|J|J|J|J|Y|  
|[lastIndexOf\-Methode \(Array\)](../../javascript/reference/lastindexof-method-array-javascript.md)|N|N|J|J|J|J|Y|  
|[lastIndexOf\-Methode \(String\)](../../javascript/reference/lastindexof-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[lastMatch\-Eigenschaft \($&\)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)|Y|J|J|J|J|J|Y|  
|[lastParen\-Eigenschaft \($\+\)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)|Y|J|J|J|J|J|Y|  
|[lbound\-Methode](../../javascript/reference/lbound-method-vbarray-javascript.md)|Y|J|J|J|J|J|Y|  
|[leftContext\-Eigenschaft \($'\)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)|Y|J|J|J|J|J|Y|  
|[Left Shift\-Zuweisungsoperator \(\<\<\=\)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[length\-Eigenschaft \(Arguments\)](../../javascript/reference/length-property-arguments-javascript.md)|Y|J|J|J|J|J|Y|  
|[length\-Eigenschaft \(Array\)](../../javascript/reference/length-property-array-javascript.md)|Y|J|J|J|J|J|Y|  
|[length\-Eigenschaft \(Funktion\)](../../javascript/reference/length-property-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[length\-Eigenschaft \(String\)](../../javascript/reference/length-property-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[Operator Kleiner als \(\<\)](../../javascript/reference/comparison-operators-javascript.md)|Y|J|J|J|J|J|Y|  
|[Operator Kleiner gleich \(\<\=\)](../../javascript/reference/comparison-operators-javascript.md)|Y|J|J|J|J|J|Y|  
|[let\-Anweisung](../../javascript/reference/let-statement-javascript.md)|N|N|N|N|J|Y|V8: N<br />V8.1: J|  
|[link\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|Y|  
|[LN2\-Konstante](../../javascript/reference/math-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[LN10\-Konstante](../../javascript/reference/math-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[localeCompare\-Methode](../../javascript/reference/localecompare-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[log\-Funktion](../../javascript/reference/math-log-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[LOG2E\-Konstante](../../javascript/reference/math-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[LOG10E\-Konstante](../../javascript/reference/math-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[Logischer AND\-Operator \(&&\)](../../javascript/reference/logical-and-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[Logischer NOT\-Operator \(\!\)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|Y|J|J|J|J|J|Y|  
|[Logischer OR\-Operator \(&#124;&#124;\)](../../javascript/reference/logical-or-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[map\-Methode](../../javascript/reference/map-method-array-javascript.md)|N|N|J|J|J|J|Y|  
|[Map\-Objekt](../../javascript/reference/map-object-javascript.md)|N|N|N|N|J|Y|V8: N<br />V8.1: J|  
|[match\-Methode](../../javascript/reference/match-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[Math\-Objekt](../../javascript/reference/math-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[max\-Funktion](../../javascript/reference/math-max-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[MAX\_VALUE\-Konstante](../../javascript/reference/number-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[message\-Eigenschaft](../../javascript/reference/message-property-error-javascript.md)|Y|J|J|J|J|J|Y|  
|[min\-Funktion](../../javascript/reference/math-min-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[MIN\_VALUE\-Konstante](../../javascript/reference/number-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[Modulozuweisungsoperator \(%\=\)](../../javascript/reference/modulus-assignment-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[Operator Modulo \(%\)](../../javascript/reference/modulus-operator-decrementjavascript.md)|Y|J|J|J|J|J|Y|  
|[moveFirst\-Methode](../../javascript/reference/movefirst-method-enumerator-javascript.md)|Y|J|J|J|J|J|Y|  
|[moveNext\-Methode](../../javascript/reference/movenext-method-enumerator-javascript.md)|Y|J|J|J|J|J|Y|  
|[multiline\-Eigenschaft](../../javascript/reference/multiline-property-regular-expression-javascript.md)|Y|J|J|J|J|J|Y|  
|[Multiplikationszuweisungsoperator \(\*\=\)](../../javascript/reference/multiplication-assignment-operator-decrement-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[Multiplikationsoperator \(\*\)](../../javascript/reference/multiplication-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[name\-Eigenschaft](../../javascript/reference/name-property-error-javascript.md)|Y|J|J|J|J|J|Y|  
|[NaN\-Konstante \(Global\)](../../javascript/reference/nan-constant-javascript.md)|Y|J|J|J|J|J|Y|  
|[NaN\-Konstante \(Number\)](../../javascript/reference/number-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[NEGATIVE\_INFINITY\-Konstante](../../javascript/reference/number-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[new\-Operator](../../javascript/reference/new-operator-decrementjavascript.md)|Y|J|J|J|J|J|Y|  
|[Nichtidentitätsoperator \(\!\=\=\)](../../javascript/reference/comparison-operators-javascript.md)|Y|J|J|J|J|J|Y|  
|[now\-Funktion](../../javascript/reference/date-now-function-javascript.md)|N|N|J|J|J|J|Y|  
|[Number\-Objekt](../../javascript/reference/number-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[number\-Eigenschaft](../../javascript/reference/number-property-error-javascript.md)|Y|J|J|J|J|J|Y|  
|[Object\-Objekt](../../javascript/reference/object-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)|Y|J|J|J|J|J|Y|  
|[Date.parse\-Funktion](../../javascript/reference/date-parse-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[JSON.parse\-Funktion](../../javascript/reference/json-parse-function-javascript.md)|N|J|J|J|J|J|Y|  
|[parseFloat\-Funktion](../../javascript/reference/parsefloat-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[parseInt\-Funktion](../../javascript/reference/parseint-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[PI\-Konstante](../../javascript/reference/math-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[pop\-Methode](../../javascript/reference/pop-method-array-javascript.md)|Y|J|J|J|J|J|Y|  
|[POSITIVE\_INFINITY\-Konstante](../../javascript/reference/number-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[pow\-Funktion](../../javascript/reference/math-pow-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[preventExtensions\-Funktion](../../javascript/reference/object-preventextensions-function-javascript.md)|N|N|J|J|J|J|Y|  
|[Promise\-Objekt](../../javascript/reference/promise-object-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[prototype\-Eigenschaft](../../javascript/reference/prototype-property-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[propertyIsEnumerable\-Methode](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[Proxy\-Objekt](../../javascript/reference/proxy-object-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[push\-Methode](../../javascript/reference/push-method-array-javascript.md)|Y|J|J|J|J|J|Y|  
|[random\-Funktion](../../javascript/reference/math-random-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[raw\-Funktion](../../javascript/reference/string-raw-function-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[reduce\-Methode](../../javascript/reference/reduce-method-array-javascript.md)|N|N|J|J|J|J|Y|  
|[reduceRight\-Methode](../../javascript/reference/reduceright-method-array-javascript.md)|N|N|J|J|J|J|Y|  
|[RegExp\-Objekt](../../javascript/reference/regexp-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[Syntax regulärer Ausdrücke](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)|Y|J|J|J|J|J|Y|  
|[Regulärausdruck\/y\-Flag](../../javascript/reference/regular-expression-object-javascript.md)|N|N|N|N|N|Exp.|V8.1: N<br />V10: Exp.|  
|[repeat\-Methode \(String\)](../../javascript/reference/repeat-method-string-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[replace\-Methode](../../javascript/reference/replace-method-string-javascript.md)|Y|J|J|J|J|J|J|  
|[Funktionen](../../javascript/functions-javascript.md)|N|N|N|N|N|N|V8.1: N<br />V10: J|  
|[return\-Anweisung](../../javascript/reference/return-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[reverse\-Methode](../../javascript/reference/reverse-method-javascript.md)|Y|J|J|J|J|J|Y|  
|[rightContext\-Eigenschaft \($'\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)|Y|J|J|J|J|J|Y|  
|[Right Shift\-Zuweisungsoperator \(\>\>\=\)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[round\-Funktion](../../javascript/reference/math-round-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[ScriptEngine\-Funktion](../../javascript/reference/scriptengine-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[ScriptEngineBuildVersion\-Funktion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[ScriptEngineMajorVersion\-Funktion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[ScriptEngineMinorVersion\-Funktion](../../javascript/reference/scriptengineminorversion-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[seal\-Funktion](../../javascript/reference/object-seal-function-javascript.md)|N|N|J|J|J|J|Y|  
|[search\-Methode](../../javascript/reference/search-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[Set\-Objekt](../../javascript/reference/set-object-javascript.md)|N|N|N|N|J|Y|V8: N<br />V8.1: J|  
|[setDate\-Methode](../../javascript/reference/setdate-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setFullYear\-Methode](../../javascript/reference/setfullyear-method-date-javascript.md)||Y|J|J|J|J|Y|  
|[setHours\-Methode](../../javascript/reference/sethours-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setMilliseconds\-Methode](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setMinutes\-Methode](../../javascript/reference/setminutes-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setMonth\-Methode](../../javascript/reference/setmonth-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setSeconds\-Methode](../../javascript/reference/setseconds-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setTime\-Methode](../../javascript/reference/settime-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setUTCDate\-Methode](../../javascript/reference/setutcdate-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setUTCFullYear\-Methode](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setUTCHours\-Methode](../../javascript/reference/setutchours-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setUTCMilliseconds\-Methode](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setUTCMinutes\-Methode](../../javascript/reference/setutcminutes-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setUTCMonth\-Methode](../../javascript/reference/setutcmonth-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setUTCSeconds\-Methode](../../javascript/reference/setutcseconds-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[setYear\-Methode](../../javascript/reference/setyear-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[shift\-Methode](../../javascript/reference/shift-method-array-javascript.md)|Y|J|J|J|J|J|Y|  
|[sin\-Funktion](../../javascript/reference/math-sin-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[slice\-Methode \(Array\)](../../javascript/reference/slice-method-array-javascript.md)|Y|J|J|J|J|J|Y|  
|[slice\-Methode \(String\)](../../javascript/reference/slice-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[small\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|Y|  
|[some\-Methode](../../javascript/reference/some-method-array-javascript.md)|N|N|J|J|J|J|Y|  
|[sort\-Methode](../../javascript/reference/sort-method-array-javascript.md)|Y|J|J|J|J|J|Y|  
|[source\-Eigenschaft](../../javascript/reference/source-property-regular-expression-javascript.md)|Y|J|J|J|J|J|Y|  
|[splice\-Methode](../../javascript/reference/splice-method-array-javascript.md)|Y|J|J|J|J|J|Y|  
|[split\-Methode](../../javascript/reference/split-method-string-javascript.md)|Y|J|J|J|J|J|J|  
|[Funktionen](../../javascript/functions-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[sqrt\-Funktion](../../javascript/reference/math-sqrt-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[SQRT1\_2\-Konstante](../../javascript/reference/math-constants-javascript.md)|Y|J|J|J|J|J|Y|  
|[SQRT2\-Konstante](../../javascript/reference/math-constants-javascript.md)|Y|J|J|J|J|J|J|  
|[Use Strict\-Direktive](../../javascript/reference/use-strict-directive.md)|N|N|N|J|J|J|Y|  
|[strike\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|Y|  
|[String\-Objekt](../../javascript/reference/string-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[JSON.stringify\-Funktion](../../javascript/reference/json-stringify-function-javascript.md)|N|J|J|J|J|J|Y|  
|[sub\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|Y|  
|[substr\-Methode](../../javascript/reference/substr-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[substring\-Methode](../../javascript/reference/substring-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[Subtraktionszuweisungsoperator \(\-\=\)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[Subtraktionsoperator \(\-\)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[sup\-Methode](../../javascript/reference/html-tag-methods-javascript.md)|Y|J|J|J|J|J|Y|  
|[switch\-Anweisung](../../javascript/reference/switch-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[Symbol\-Objekt](../../javascript/reference/symbol-object-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[tan\-Funktion](../../javascript/reference/math-tan-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[Vorlagenzeichenfolgen](../../javascript/advanced/template-strings-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[test\-Methode](../../javascript/reference/test-method-regular-expression-javascript.md)|Y|J|J|J|J|J|Y|  
|[this\-Anweisung](../../javascript/reference/this-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[throw\-Anweisung](../../javascript/reference/throw-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[toArray\-Methode](../../javascript/reference/toarray-method-vbarray-javascript.md)|Y|J|J|J|J|J|Y|  
|[toDateString\-Methode](../../javascript/reference/todatestring-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[toExponential\-Methode](../../javascript/reference/toexponential-method-number-javascript.md)|Y|J|J|J|J|J|Y|  
|[toFixed\-Methode](../../javascript/reference/tofixed-method-number-javascript.md)|Y|J|J|J|J|J|Y|  
|[toGMTString\-Methode](../../javascript/reference/togmtstring-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[toISOString\-Methode](../../javascript/reference/toisostring-method-date-javascript.md)|N|N|J|J|J|J|Y|  
|[toJSON\-Methode](../../javascript/reference/tojson-method-date-javascript.md)|N|J|J|J|J|J|Y|  
|[toLocaleDateString\-Methode](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[toLocaleLowercase\-Methode](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[toLocaleString\-Methode](../../javascript/reference/tolocalestring-method-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[toLocaleTimeString\-Methode](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[toLocaleUppercase\-Methode](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[toLowerCase\-Methode](../../javascript/reference/tolowercase-method-javascript.md)|Y|J|J|J|J|J|Y|  
|[toPrecision\-Methode](../../javascript/reference/toprecision-method-number-javascript.md)|Y|J|J|J|J|J|Y|  
|[toString\-Methode](../../javascript/reference/tostring-method-object-javascript.md)|Y|J|J|J|J|J|Y|  
|[toTimeString\-Methode](../../javascript/reference/totimestring-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[toUpperCase\-Methode](../../javascript/reference/touppercase-method-string-javascript.md)|Y|J|J|J|J|J|Y|  
|[toUTCString\-Methode](../../javascript/reference/toutcstring-method-date-javascript.md)|Y|J|J|J|J|J|Y|  
|[trim\-Methode](../../javascript/reference/trim-method-string-javascript.md)|N|N|J|J|J|J|Y|  
|[try\-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[typeof\-Operator](../../javascript/reference/typeof-operator-decrementjavascript.md)|Y|J|J|J|J|J|Y|  
|[ubound\-Methode](../../javascript/reference/ubound-method-vbarray-javascript.md)|Y|J|J|J|J|J|J|  
|[Uint8Array\-Objekt](../../javascript/reference/uint8array-object.md)|N|N|N|J|J|J|J|  
|[Uint16Array\-Objekt](../../javascript/reference/uint16array-object.md)|N|N|N|J|J|J|J|  
|[Uint32Array\-Objekt](../../javascript/reference/uint32array-object.md)|N|N|N|J|J|J|J|  
|[Uint8ClampedArray\-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)|N|N|N|N|J|Y|V8: Nein<br />V8.1 \(Win\): Ja<br />V8.1 \(Phone\): Nein<br />V10: J|  
|[Unärer Negationsoperator \(\-\)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|Y|J|J|J|J|J|Y|  
|[undefined\-Konstante](../../javascript/reference/undefined-constant-javascript.md)|Y|J|J|J|J|J|Y|  
|[unescape\-Funktion](../../javascript/reference/unescape-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[Unicode\-Codepunkt\-Escape\-Zeichen](../../javascript/advanced/special-characters-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[unshift\-Methode](../../javascript/reference/unshift-method-array-javascript.md)|Y|J|J|J|J|J|Y|  
|[Vorzeichenloser Right Shift\-Zuweisungsoperator \(\>\>\>\=\)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)|Y|J|J|J|J|J|Y|  
|[Vorzeichenloser Right Shift\-Operator \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|Y|J|J|J|J|J|J|  
|[Use Strict\-Direktive](../../javascript/reference/use-strict-directive.md)|N|N|N|J|J|J|Y|  
|[UTC\-Funktion](../../javascript/reference/date-utc-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[valueOf\-Methode](../../javascript/reference/valueof-method-object-javascript.md)|Y|J|J|J|J|J|J|  
|[values\-Methode \(Array\)](../../javascript/reference/values-method-array-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[var\-Anweisung](../../javascript/reference/var-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[VBArray\-Objekt](../../javascript/reference/vbarray-object-javascript.md)|Y|J|J|J|J|J|N|  
|[void\-Operator](../../javascript/reference/void-operator-decrementjavascript.md)|Y|J|J|J|J|J|Y|  
|[WeakMap\-Objekt](../../javascript/reference/weakmap-object-javascript.md)|N|N|N|N|J|Y|V8: N<br />V8.1: J|  
|[WeakSet\-Objekt](../../javascript/reference/weakset-object-javascript.md)|N|N|N|N|N|Y|V8.1: N<br />V10: J|  
|[while\-Anweisung](../../javascript/reference/while-statement-javascript.md)|Y|J|J|J|J|J|J|  
|[WinRTError\-Objekt](../../javascript/reference/winrterror-object-javascript.md)|N|N|N|J|J|J|Y|  
|[with\-Anweisung](../../javascript/reference/with-statement-javascript.md)|Y|J|J|J|J|J|Y|  
|[write\-Funktion](../../javascript/reference/debug-write-function-javascript.md)|Y|J|J|J|J|J|Y|  
|[writeln\-Funktion](../../javascript/reference/debug-writeln-function-javascript.md)|Y|J|J|J|J|J|J|  
  
 \* Unterstützt DOM\-Objekte, jedoch keine benutzerdefinierten Objekte. Die Attribute `enumerable` und `configurable` können angegeben werden, werden jedoch nicht verwendet.  
  
## Siehe auch  
 [Definieren der Dokumentkompatibilität](http://go.microsoft.com/fwlink/?LinkId=208537)
---
title: "JavaScript-Laufzeitfehler | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT-32725"
  - "VS.WebClient.Help.SCRIPT7002"
  - "VS.WebClient.Help.SCRIPT1001"
  - "VS.WebClient.Help.SCRIPT16389"
  - "VS.WebClient.HelpSCRIPT50"
  - "VS.WebClient.HelpSCRIPT70"
  - "VS.WebClient.HelpSCRIPT87"
  - "VS.WebClient.HelpSCRIPT65535"
  - "VS.WebClient.HelpSCRIPT445"
  - "VS.WebClient.HelpSCRIPT600"
  - "VS.WebClient.HelpSCRIPT2343"
  - "VS.WebClient.HelpSCRIPT122"
  - "VS.WebClient.HelpSCRIPT28"
  - "VS.WebClient.HelpSCRIPT16386"
  - "VS.WebClient.HelpSCRIPT7015"
  - "VS.WebClient.HelpSCRIPT3"
  - "VS.WebClient.HelpSCRIPT16388"
  - "VS.WebClient.HelpSCRIPT14"
  - "VS.WebClient.HelpSCRIPT12030"
  - "VS.WebClient.HelpSCRIPT12029"
  - "VS.WebClient.HelpSCRIPT1001"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Fehler [JavaScript]"
  - "Laufzeitfehler, JavaScript"
ms.assetid: c111469d-8f31-4bde-9d46-16d58775db7d
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# JavaScript-Laufzeitfehler
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Laufzeitfehler treten auf, wenn das Skript versucht, eine Aktion durchzuführen, die das System nicht ausführen kann. Laufzeitfehler können z. B. beim Auswerten von variablen Ausdrücken oder beim Zuordnen von Arbeitsspeicher auftreten.  
  
## Windows\-Runtime\-Fehler  
 Wenn Sie Windows\-Runtime\-APIs in Ihrer [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-App verwenden, werden möglicherweise JavaScript\-Fehler angezeigt, die aus Windows\-Runtime\-HRESULTs konvertiert wurden. Windows\-Runtime\-HRESULTs im Bereich über 0x80070000 werden in JavaScript\-Fehler konvertiert, indem der Hexadezimalwert der niedrigen Bits in einen Dezimalwert konvertiert wird. So wird beispielsweise das HRESULT 0x80070032 in den Dezimalwert 50 konvertiert, und der JavaScript\-Fehler lautet SCRIPT50. Das HRESULT 0x80074005 wird in den Dezimalwert 16389 konvertiert, und der JavaScript\-Fehler lautet SCRIPT16389.  
  
## Fehler  
  
|Fehlernummer|Beschreibung|  
|------------------|------------------|  
|5|[Zugriff verweigert](../../javascript/misc/access-is-denied.md)|  
|438|[Das Objekt unterstützt diese Eigenschaft oder Methode nicht.](../../javascript/misc/object-doesn-t-support-this-property-or-method.md)|  
|1001|Nicht genügend Arbeitsspeicher|  
|5029|[Die Arraylänge muss eine endliche positive Ganzzahl sein.](../../javascript/misc/array-length-must-be-a-finite-positive-integer.md)|  
|5030|[Der Arraylänge muss eine endliche positive Ganzzahl zugewiesen sein.](../../javascript/misc/array-length-must-be-assigned-a-finite-positive-number.md)|  
|5028|[Array\- oder arguments\-Objekt erwartet](../../javascript/misc/array-or-arguments-object-expected.md)|  
|5010|[Boolescher Wert erwartet](../../javascript/misc/boolean-expected.md)|  
|5003|[Zuweisen zu einem Funktionsergebnis nicht möglich](../../javascript/misc/cannot-assign-to-a-function-result.md)|  
|5000|[Zuweisen zu „this“ nicht möglich](../../javascript/misc/cannot-assign-to-this.md)|  
|5034|[Zirkelverweis in Wertargument nicht unterstützt](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|  
|5006|[Date\-Objekt erwartet](../../javascript/misc/date-object-expected.md)|  
|5015|[Enumerator\-Objekt erwartet](../../javascript/misc/enumerator-object-expected.md)|  
|5022|[Ausnahme ausgelöst und nicht abgefangen](../../javascript/misc/exception-thrown-and-not-caught.md)|  
|5020|[„\)“ in regulärem Ausdruck erwartet](../../javascript/misc/expected-right-parenthesis-in-regular-expression-javascript.md)|  
|5019|[„&#93;“ in regulärem Ausdruck erwartet](../../javascript/misc/expected-right-square-bracket-in-regular-expression-javascript.md)|  
|5023|[Funktion enthält kein gültiges prototype\-Objekt.](../../javascript/misc/function-does-not-have-a-valid-prototype-object.md)|  
|5002|[Funktion erwartet](../../javascript/misc/function-expected.md)|  
|5008|[Ungültige Zuweisung](../../javascript/misc/illegal-assignment-javascript.md)|  
|5021|[Ungültiger Bereich in Zeichensatz](../../javascript/misc/invalid-range-in-character-set-javascript.md)|  
|5035|[Ungültiges replacer\-Argument](../../javascript/misc/invalid-replacer-argument.md)|  
|5014|[JavaScript\-Objekt erwartet](../../javascript/misc/javascript-object-expected.md)|  
|5001|[Zahl erwartet](../../javascript/misc/number-expected.md)|  
|5007|[Objekt erwartet](../../javascript/misc/object-expected.md)|  
|5012|[Objektmember erwartet](../../javascript/misc/object-member-expected.md)|  
|5016|[Reguläres Ausdrucksobjekt erwartet](../../javascript/misc/regular-expression-object-expected.md)|  
|5005|[Zeichenfolge erwartet](../../javascript/misc/string-expected.md)|  
|5017|[Syntaxfehler in regulärem Ausdruck](../../javascript/misc/syntax-error-in-regular-expression-javascript.md)|  
|5026|[Die Anzahl der Dezimalstellen liegt außerhalb des gültigen Bereichs.](../../javascript/misc/the-number-of-fractional-digits-is-out-of-range.md)|  
|5027|[Die Genauigkeit liegt außerhalb des gültigen Bereichs.](../../javascript/misc/the-precision-is-out-of-range.md)|  
|5025|[Der zu decodierende URI weist keine gültige Codierung auf.](../../javascript/misc/the-uri-to-be-decoded-is-not-a-valid-encoding.md)|  
|5024|[Der zu codierende URI enthält ein ungültiges Zeichen.](../../javascript/misc/the-uri-to-be-encoded-contains-an-invalid-character.md)|  
|5009|[Nicht definierter Bezeichner](../../javascript/misc/undefined-identifier.md)|  
|5018|[Unerwarteter Quantifizierer](../../javascript/misc/unexpected-quantifier-javascript.md)|  
|5013|[VBArray erwartet](../../javascript/misc/vbarray-expected.md)|  
  
## Siehe auch  
 [JavaScript\-Syntaxfehler](../../javascript/reference/javascript-syntax-errors.md)
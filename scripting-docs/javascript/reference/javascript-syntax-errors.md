---
title: JavaScript-Syntaxfehler | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- syntax errors, JavaScript
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bc3398d6a90ef308fd2b4b367bc1006ad95f5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-syntax-errors"></a>JavaScript-Syntaxfehler
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Syntaxfehler treten bei der die Struktur eines Ihrer [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Anweisungen verstößt gegen eine oder mehrere der syntaktischen Regeln.  
  
## <a name="errors"></a>Fehler  
  
|Fehlernummer|Beschreibung|  
|------------------|-----------------|  
|1019|[„break“ ist außerhalb der Schleife unzulässig](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[„continue“ ist außerhalb der Schleife unzulässig](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[Die bedingte Kompilierung ist deaktiviert](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|[„default“ darf in einer switch-Anweisung nur einmal angegeben werden](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[Erwartet ' ('](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[Erwartet ')'](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[Erwartet '/'](../../javascript/misc/expected-minus.md)|  
|1003|[„:“ erwartet](../../javascript/misc/expected-colon.md)|  
|1004|[„;“ erwartet](../../javascript/misc/expected-semicolon.md)|  
|1032|[„@“ erwartet](../../javascript/misc/expected-at.md)|  
|1029|[„@end“ erwartet](../../javascript/misc/expected-at-end.md)|  
|1007|[Erwartet ' &#93; "](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[„{“ erwartet](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|[„}“ erwartet](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|["=" Erwartet](../../javascript/misc/expected-equal-javascript.md)|  
|1033|[„catch“ erwartet](../../javascript/misc/expected-catch.md)|  
|1031|[Konstante erwartet](../../javascript/misc/expected-constant.md)|  
|1023|[Hexadezimalzahl erwartet](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Bezeichner erwartet.](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Es wurde ein Bezeichner, eine Zeichenfolge oder eine Zahl erwartet](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|[„while“ erwartet](../../javascript/misc/expected-while.md)|  
|1014|[Ungültige Zeichen](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[Die Bezeichnung wurde nicht gefunden](../../javascript/misc/label-not-found.md)|  
|1025|[Die Bezeichnung wurde neu definiert](../../javascript/misc/label-redefined.md)|  
|1018|[return-Anweisung ist außerhalb der Funktion](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Syntaxfehler](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[Auf „throw“ muss ein Ausdruck in derselben Quellzeile folgen](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Nicht abgeschlossener Kommentar](../../javascript/misc/unterminated-comment.md)|  
|1015|[Nicht abgeschlossene Zeichenfolgenkonstante.](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### <a name="script-host-errors"></a>Host Skriptfehler  
 Die folgenden Fehler sind Fehler bezieht sich auf der Skripthost ordnungsgemäß sprechen, aber sie möglicherweise gelegentlich angezeigt.  
  
|Fehler|HRESULT|Beschreibung|  
|-----------|-------------|-----------------|  
|SCRIPT_E_RECORDED|0x86664004|Ein Fehler wurde aufgezeichnet, um zwischen Skriptmodul und Host übergeben werden. Der Host muss den Fehlercode an dem Aufrufer übergeben.|  
|SCRIPT_E_REPORTED|0 x 80020101|Skript-Modul hat eine nicht behandelte Ausnahme an den Host über IActiveScriptSite::OnScriptError gemeldet. Host kann diesen Fehler ignorieren.|  
|SCRIPT_E_PROPAGATE|0x8002010|Ein Skriptfehler wird an den Aufrufer weitergegeben, die in einem anderen Thread möglicherweise. Der Host sollte den Fehlercode an dem Aufrufer übergeben werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md)
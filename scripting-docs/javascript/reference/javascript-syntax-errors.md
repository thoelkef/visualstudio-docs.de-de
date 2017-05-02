---
title: "JavaScript-Syntaxfehler | Microsoft Docs"
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
  - "JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Fehler [JavaScript]"
  - "Syntaxfehler, JavaScript"
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# JavaScript-Syntaxfehler
[!INCLUDE[javascript](../../includes/javascript-md.md)]\-Syntaxfehler treten auf, wenn die Struktur einer der [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Anweisungen gegen mindestens eine syntaktische Regel verstößt.  
  
## Fehler  
  
|Fehlernummer|Beschreibung|  
|------------------|------------------|  
|1019|["break" ist außerhalb der Schleife unzulässig.](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|["continue" ist außerhalb der Schleife unzulässig.](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[Die bedingte Kompilierung ist ausgeschaltet.](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|["default" darf in einer switch\-Anweisung nur einmal angegeben werden.](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|["\(" erwartet.](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|["\)" erwartet.](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|["\/" erwartet.](../../javascript/misc/expected-minus.md)|  
|1003|[":" erwartet.](../../javascript/misc/expected-colon.md)|  
|1004|[";" erwartet.](../../javascript/misc/expected-semicolon.md)|  
|1032|["@" erwartet.](../../javascript/misc/expected-at.md)|  
|1029|["@end" erwartet.](../../javascript/misc/expected-at-end.md)|  
|1007|["&#93;" erwartet.](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|["{" erwartet.](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|["}" erwartet.](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|["\=" erwartet.](../../javascript/misc/expected-equal-javascript.md)|  
|1033|["catch" erwartet.](../../javascript/misc/expected-catch.md)|  
|1031|[Konstante erwartet.](../../javascript/misc/expected-constant.md)|  
|1023|[Hexadezimalzahl erwartet.](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Bezeichner erwartet.](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Es wurde ein Bezeichner, eine Zeichenfolge oder eine Zahl erwartet.](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|["while" erwartet.](../../javascript/misc/expected-while.md)|  
|1014|[Ungültiges Zeichen.](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[Die Bezeichnung wurde nicht gefunden.](../../javascript/misc/label-not-found.md)|  
|1025|[Die Bezeichnung wurde neu definiert.](../../javascript/misc/label-redefined.md)|  
|1018|[return\-Anweisung ist außerhalb der Funktion.](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Syntaxfehler.](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[Auf Throw muss ein Ausdruck in derselben Quellzeile folgen.](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Nicht abgeschlossener Kommentar.](../../javascript/misc/unterminated-comment.md)|  
|1015|[Nicht abgeschlossene Zeichenfolgenkonstante.](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### Script Host\-Fehler  
 Die folgenden Fehler betreffen streng genommen den Script Host. Sie können jedoch gelegentlich angezeigt werden.  
  
|Fehler|HRESULT|Beschreibung|  
|------------|-------------|------------------|  
|SCRIPT\_E\_RECORDED|0x86664004|Es wurde ein Fehler aufgezeichnet, der vom Skriptmodul an den Host übergeben werden soll.  Der Host muss den Fehlercode an den Aufrufer übergeben.|  
|SCRIPT\_E\_REPORTED|0x80020101|Das Skriptmodul hat über IActiveScriptSite::OnScriptError einen Ausnahmefehler an den Host gemeldet.  Der Host kann diesen Fehler ignorieren.|  
|SCRIPT\_E\_PROPAGATE|0x8002010|Ein Skriptfehler wird an den Aufrufer weitergegeben, der sich möglicherweise in einem anderen Thread befindet.  Der Host sollte den Fehlercode an den Aufrufer übergeben.|  
  
## Siehe auch  
 [JavaScript\-Laufzeitfehler](../../javascript/reference/javascript-run-time-errors.md)
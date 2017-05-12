---
title: "@if-Anweisung (JavaScript) | Microsoft Docs"
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
  - "@if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@if-Anweisung"
  - "Bedingungsanweisungen, if"
  - "ELIF-Anweisung"
  - "else-Anweisung"
  - "if-Anweisung, @if"
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# @if-Anweisung (JavaScript)
Führt bedingt eine Gruppe von Anweisungen aus, abhängig vom Wert eines Ausdrucks.  
  
> [!WARNING]
>  Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 11 und den [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps nicht unterstützt.  Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 10 und allen früheren Versionen unterstützt.  
  
## Syntax  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## Parameter  
 *condition1, condition2*  
 Optional.  Ein Ausdruck, der in einen booleschen Ausdruck konvertiert werden kann.  
  
 `text1`  
 Dies ist optional.  Der zu analysierende Text, wenn `condition1` den Wert **true** hat.  
  
 `text2`  
 Dies ist optional.  Der zu analysierende Text, wenn `condition1` den Wert **false** und `condition2` den Wert **true** hat.  
  
 `text3`  
 Dies ist optional.  Der zu analysierende Text, wenn `condition1` und `condition2` den Wert **false** haben.  
  
## Hinweise  
 Beim Schreiben einer `@if`\-Anweisung müssen Klauseln nicht in getrennten Zeilen eingegeben werden.  Sie können mehrere **@elif**\-Klauseln verwenden.  In diesem Fall müssen alle **@elif**\-Klauseln jedoch vor der **@else**\-Klausel aufgeführt sein.  
  
 In der Regel legen Sie mit der `@if`\-Anweisung fest, welcher Text unter mehreren Optionen für die Textausgabe verwendet werden soll.  
  
 Bedingte Kompilierungsvariablen werden nur selten in Skripts verwendet, die für ASP\- oder ASP.NET\-Seiten oder Befehlszeilenprogramme geschrieben wurden.  Der Grund dafür besteht darin, dass die Funktionen der Compiler mit anderen Methoden bestimmt werden können.  
  
 Fügen Sie beim Schreiben eines Skripts für eine Webseite den Code für die bedingte Kompilierung stets in Kommentaren hinzu.  Dadurch können Hosts, die die bedingte Kompilierung nicht unterstützen, diesen Code ignorieren.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der Anweisung **@if...@elif…@else...@end**.  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## Anforderungen  
 Wird in allen Versionen von Internet Explorer, jedoch nicht in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps unterstützt.  
  
## Siehe auch  
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc\_on\-Anweisung](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set\-Anweisung](../../javascript/reference/at-set-statement-javascript.md)
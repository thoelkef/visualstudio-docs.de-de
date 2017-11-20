---
title: '@ifAnweisung (JavaScript) | Microsoft Docs'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '@if_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- elif statement
- conditional statements, if
- if statement, @if
- else statement
- '@if statement'
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87cfc157ab16b183ccf687fa221393be4ab74757
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="if-statement-javascript"></a>@ifAnweisung (JavaScript)
Führt bedingt eine Gruppe von Anweisungen aus, abhängig vom Wert eines Ausdrucks.  
  
> [!WARNING]
>  Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 11 und den [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]-Apps nicht unterstützt. Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 10 und allen früheren Versionen unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="parameters"></a>Parameter  
 *condition1 condition2 den Wert*  
 Dies ist optional. Ein Ausdruck, der in einen booleschen Ausdruck konvertiert werden kann.  
  
 `text1`  
 Dies ist optional. Text, die analysiert werden, wenn `condition1` ist **"true"**.  
  
 `text2`  
 Dies ist optional. Text, die analysiert werden, wenn `condition1` ist **"false"** und `condition2` ist **"true"**.  
  
 `text3`  
 Dies ist optional. Text, die analysiert werden, wenn beide `condition1` und `condition2` sind **"false"**.  
  
## <a name="remarks"></a>Hinweise  
 Beim Schreiben einer `@if`-Anweisung müssen Klauseln nicht in getrennten Zeilen eingegeben werden. Sie können mehrere  **@elif**  Klauseln. Allerdings alle  **@elif**  Klauseln müssen ergeben, vor einem  **@else**  Klausel.  
  
 In der Regel legen Sie mit der `@if`-Anweisung fest, welcher Text unter mehreren Optionen für die Textausgabe verwendet werden soll.  
  
 Bedingte Kompilierungsvariablen werden nur selten in Skripts verwendet, die für ASP- oder ASP.NET-Seiten oder Befehlszeilenprogramme geschrieben wurden. Der Grund dafür besteht darin, dass die Funktionen der Compiler mit anderen Methoden bestimmt werden können.  
  
 Fügen Sie beim Schreiben eines Skripts für eine Webseite den Code für die bedingte Kompilierung stets in Kommentaren hinzu. Dadurch können Hosts, die die bedingte Kompilierung nicht unterstützen, diesen Code ignorieren.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der  **@if...@elif... @else... @end**  Anweisung.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 Wird in allen Versionen von Internet Explorer, jedoch nicht in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]-Apps unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variablen für die bedingte Kompilierung](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onAnweisung](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set-Anweisung](../../javascript/reference/at-set-statement-javascript.md)
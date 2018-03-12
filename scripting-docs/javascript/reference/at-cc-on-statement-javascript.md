---
title: '@cc_onAnweisung (JavaScript) | Microsoft Docs'
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
- '@cc_on_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, activating
- '@cc_on statement'
- '@set statement'
- '@if statement'
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e993d5bc8302931a5722495da70612e79f7dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ccon-statement-javascript"></a>@cc_onAnweisung (JavaScript)
Aktiviert die Unterstützung für die bedingte Kompilierung in Skriptkommentaren.  
  
> [!WARNING]
>  Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 11 und den [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]-Apps nicht unterstützt. Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 10 und allen früheren Versionen unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
@cc_on   
```  
  
## <a name="remarks"></a>Hinweise  
 Die `@cc_on`-Anweisung aktiviert die bedingte Kompilierung in Skriptkommentaren.  
  
 Weniger gebräuchlich ist die Verwendung von Variablen für die bedingte Kompilierung in Skripts, die für ASP- oder ASP.NET-Seiten oder Befehlszeilenprogramme geschrieben wurden, da die Fähigkeiten der Compiler mit anderen Methoden bestimmt werden können.  
  
 Fügen Sie beim Schreiben eines Skripts für eine Webseite den Code für die bedingte Kompilierung stets in Kommentaren hinzu. Dadurch können Hosts, die die bedingte Kompilierung nicht unterstützen, diesen Code ignorieren.  
  
 In einem Kommentar sollte unbedingt die `@cc_on`-Anweisung verwendet werden, sodass Browser, die keine bedingte Kompilierung unterstützen, das Skript als gültige Syntax annehmen:  
  
 Mit einer `@if`- oder `@set`-Anweisung lässt sich die bedingte Kompilierung auch außerhalb von Kommentaren aktivieren.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `@cc_on`-Anweisung.  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
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
 [@ifAnweisung](../../javascript/reference/at-if-statement-javascript.md)   
 [@set-Anweisung](../../javascript/reference/at-set-statement-javascript.md)
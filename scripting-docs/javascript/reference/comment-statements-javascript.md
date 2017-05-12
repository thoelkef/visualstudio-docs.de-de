---
title: "Comment-Anweisungen (JavaScript) | Microsoft Docs"
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
  - "Comment_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "comment-Anweisungen"
  - "Kommentare, Ignorieren"
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment-Anweisungen (JavaScript)
Veranlasst den [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Parser, Kommentare zu ignorieren.  
  
## Syntax  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## Hinweise  
 Das `comment`\-Argument ist der Text eines Kommentars, den Sie in Ihr Skript einschließen möchten.  Das `condStatement`\-Argument muss verwendet werden, wenn die bedingte Kompilierung aktiviert ist.  Wenn einzeilige Kommentare verwendet werden, darf kein Leerzeichen zwischen den "\/ \/"\- und "@"\-Zeichen stehen.  
  
 Verwenden Sie Kommentare, um zu verhindern, dass Teile eines Skripts vom [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Parser gelesen werden.  Sie können Kommentare für erläuternde Hinweise in einem Programm verwenden.  
  
 Wenn einzeilige Kommentare verwendet werden, ignoriert der Parser Text zwischen den Kommentarzeichen und dem Ende der Zeile.  Wenn mehrzeilige Kommentare verwendet werden, ignoriert der Parser Text zwischen den Start\- und Endzeichen.  
  
 Kommentare dienen zur Unterstützung der bedingten Kompilierung, wobei gleichzeitig die Kompatibilität mit Browsern beibehalten wird, die diese Funktion nicht unterstützen.  Diese Browser behandeln diese Formen von Kommentaren als einzeilige bzw. mehrzeilige Kommentare.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die häufigsten Verwendungszwecke von Kommentaren.  
  
```javascript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung einer bedingten Kompilierung gezeigt.  Dieses Beispiel enthält spezielle Kommentartrennzeichen, die nur verwendet werden, wenn die bedingte Kompilierung durch die `@cc_on`\-Anweisung aktiviert wurde.  Bei Skriptmodulen, die die bedingte Kompilierung nicht unterstützen, wird nur die Meldung angezeigt, dass die bedingte Kompilierung nicht unterstützt wird.  
  
```javascript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]
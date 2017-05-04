---
title: "Bedingte Kompilierung (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConditionalComp_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Bedingte Kompilierung"
  - "Bedingte Kompilierung, Übersicht"
ms.assetid: a843de4e-3aae-43cd-ad64-477dd00814a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Bedingte Kompilierung (JavaScript)
Die bedingte Kompilierung ermöglicht Ihnen, in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] neue Sprachfeatures zu verwenden, ohne auf die Kompatibilität mit älteren Versionen zu verzichten, die diese Features nicht unterstützen.  
  
> [!WARNING]
>  Die bedingte Kompilierung wird in allen Versionen von Internet Explorer vor Internet Explorer 11 unterstützt.  Die bedingte Kompilierung wird im Standardmodus von Internet Explorer 11 und den [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps nicht unterstützt.  
  
## Anweisungen  
 Die bedingte Kompilierung wird mit der `@cc_on`\-Anweisung oder einer `@if`\-Anweisung bzw. `@set`\-Anweisung aktiviert.  Zu den typischen Anwendungsmöglichkeiten der bedingten Kompilierung gehört das Verwenden neuer Features in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], das Einbetten von Debuggingunterstützung in ein Skript und das Verfolgen der Codeausführung.  
  
 Platzieren Sie den Code für die bedingte Kompilierung stets in Kommentaren, damit er von Hosts \(wie Netscape Navigator\), die die bedingte Kompilierung nicht unterstützen, ignoriert wird.  Im Folgenden ein Beispiel.  
  
```javascript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
 Dieses Beispiel enthält spezielle Kommentartrennzeichen, die nur verwendet werden, wenn die bedingte Kompilierung durch die `@cc_on`\-Anweisung aktiviert wurde.  Bei Skriptmodulen, die die bedingte Kompilierung nicht unterstützen, wird nur die Meldung angezeigt, dass die bedingte Kompilierung nicht unterstützt wird.
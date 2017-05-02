---
title: "escape-Funktion (JavaScript) | Microsoft Docs"
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
  - "escape"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Codieren von String-Objekten"
  - "Escape-Methode"
  - "Hexadezimal"
  - "String-Objekt, Codieren"
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# escape-Funktion (JavaScript)
Codiert Zeichenfolgen so, dass sie auf allen Computern gelesen werden können.  Veraltet.  
  
## Syntax  
  
```  
escape(charString)   
```  
  
## Hinweise  
 Das erforderliche `charString`\-Argument ist ein beliebiges zu codierendes `String`\-Objekt oder Literal.  
  
 Die **escape**\-Funktion gibt einen Zeichenfolgenwert \(im Unicodeformat\) mit dem Inhalt von `charstring` zurück.  Alle Leerzeichen, Satzzeichen, Buchstaben mit Akzenten und andere Nicht\-ASCII\-Zeichen werden durch `%`*xx*\-Codierungen ersetzt, wobei *xx* der Hexadezimalzahl des Zeichens entspricht.  Ein Leerzeichen wird beispielsweise als "%20" zurückgegeben.  
  
 Zeichen mit einem Wert über 255 werden im Format **%u** *xxxx* gespeichert.  
  
> [!NOTE]
>  Die **escape**\-Funktion sollte nicht zum Codieren von Uniform Resource Identifiers \(URIs\) verwendet werden.  Verwenden Sie stattdessen die `encodeURI`\-Funktion und die `encodeURIComponent`\-Funktion.  
  
 **Gilt für**: [Global\-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [encodeURI\-Funktion](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent\-Funktion](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)   
 [unescape\-Funktion](../../javascript/reference/unescape-function-javascript.md)
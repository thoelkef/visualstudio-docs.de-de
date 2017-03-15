---
title: "&lt;summary&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "summary-JavaScript-XML-Tag"
  - "<summary>-JavaScript-XML-Tag"
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt die Beschreibung für eine Funktion oder Methode an.  
  
## Syntax  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### Parameter  
 `locid`  
 Optional.  Der Bezeichner für Lokalisierungsinformationen über die Funktion oder Methode.  Der Bezeichner ist entweder eine Member\-ID, oder er entspricht dem `name`\-Attributwert in einem Meldungsbündel, das von OpenAjax\-Metadaten definiert wird.  Der Bezeichnertyp hängt vom Format ab, das im [\<loc\>](../ide/loc-javascript.md)\-Element angegeben ist.  
  
 `description`  
 Optional.  Eine Beschreibung der Funktion oder Methode.  
  
## Hinweise  
 Die Elemente, die verwendet werden, um Funktionen, wie unter anderem [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md) und [\<returns\>](../ide/returns-javascript.md) mit Anmerkungen zu versehen, müssen vor allen Anweisungen in den Funktionstext eingefügt werden.  
  
## Beispiel  
 Im folgenden Codebeispiel wird die Verwendung des `<summary>`\-Elements veranschaulicht.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## Siehe auch  
 [XML\-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)
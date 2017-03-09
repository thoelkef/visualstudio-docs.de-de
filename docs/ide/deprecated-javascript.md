---
title: "&lt;deprecated&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt eine veraltete Funktion oder Methode an.  
  
## Syntax  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### Parameter  
 `type`  
 Optional.  Gibt an, ob die Funktion oder Methode in einer zukünftigen Version entfernt wird oder ob die Funktion oder Methode bereits entfernt wurde und ihre Verwendung möglicherweise zu einem Fehler führen wird.  Legen Sie es auf `deprecate` fest, um anzugeben, dass die Funktion oder Methode in einer zukünftigen Version entfernt wird.  Legen Sie es auf `remove` fest, um anzugeben, dass die Funktion oder Methode bereits entfernt wurde.  
  
 `locid`  
 Optional.  Der Bezeichner für Lokalisierungsinformationen über die Funktion oder Methode.  Der Bezeichner ist entweder eine Member\-ID, oder er entspricht dem `name`\-Attributwert in einem Meldungsbündel, das von OpenAjax\-Metadaten definiert wird.  Der Bezeichnertyp hängt vom Format ab, das im [\<loc\>](../ide/loc-javascript.md)\-Element angegeben ist.  
  
 `description`  
 Optional.  Eine Beschreibung der Funktion oder Methode, die veraltet ist.  
  
## Hinweise  
 Die Elemente, die verwendet werden, um Funktionen, wie unter anderem `<deprecated>`, mit Anmerkungen zu versehen und müssen vor allen Anweisungen in den Funktionstext eingefügt werden.  Wenn Sie eine Funktion als veraltet kennzeichnen, wird empfohlen, ihr [\<summary\>](../ide/summary-javascript.md)\-Element durch das `<deprecated>`\-Element zu ersetzen.  
  
## Beispiel  
 Im folgenden Codebeispiel wird die Verwendung des `<deprecated>`\-Elements veranschaulicht.  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## Siehe auch  
 [XML\-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)
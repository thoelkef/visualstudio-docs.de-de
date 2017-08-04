---
title: "Erstellen von JSDoc-Kommentaren f&#252;r JavaScript IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Erstellen von JSDoc-Kommentaren f&#252;r JavaScript IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense in Visual Studio zeigt Informationen an, die Sie einem Skript mit standardmäßigen JSDoc\-Kommentaren hinzufügen.  Sie können JSDoc\-Kommentare verwenden, um Informationen zu Codeelementen wie z. B. Funktionen, Felder und Variablen bereitzustellen.  
  
## JSDoc\-Kommentartags  
 Die folgenden standardmäßigen JSDoc\-Kommentartags werden von IntelliSense verwendet, um Informationen zu Ihrem Code anzuzeigen.  
  
|JSDoc\-Tag|Syntax|Notizen|  
|----------------|------------|-------------|  
|@deprecated|@deprecated *Beschreibung*|Gibt eine veraltete Funktion oder Methode an.|  
|@description|@description *Beschreibung*|Gibt die Beschreibung für eine Funktion oder Methode an.|  
|@param|@param {*Typ*} *Parametername**Beschreibung*|Gibt Informationen für einen Parameter in einer Funktion oder Methode an.<br /><br /> TypeScript unterstützt auch @paramTag.|  
|@property|@property {*Typ*} *Eigenschaftsname*|Gibt Informationen an, darunter eine Beschreibung, die entweder für ein Feld oder für einen Member gilt, der über ein Objekt definiert wird.|  
|@returns|@returns {*Typ*}|Gibt einen Rückgabewert an.<br /><br /> Verwenden Sie für TypeScript @returnType statt @returns.|  
|@summary|@summary *Beschreibung*|Gibt die Beschreibung für eine Funktion oder Methode an \(identisch mit @description\).|  
|@type|@type {*Typ*}|Gibt den Typ für eine Konstante oder eine Variable an.|  
|@typedef|@typedef {*Typ*} *benutzerdefinierterTypname*|Gibt einen benutzerdefinierten Typ an.|  
  
### Beispiele  
 Das folgende Beispiel zeigt die Verwendung der JSDoc\-Tags @description, @param und @return für eine Funktion namens `getArea`.  
  
```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  
  
 Im vorhergehenden Beispiel zeigt IntelliSense die Beschreibung, Parameter und Rückgabeinformationen an, wenn Sie die öffnende Klammer für `getArea` eingeben.  
  
 ![IntelliSense&#45;Informationen für eine Funktion](~/ide/media/js_intellisense_jsdoc_comments.png "JS\_IntelliSense\_JSDoc\_Comments")  
  
 Im folgenden Beispiel wird die Verwendung des @typedef\-Tags mit dem @property\-Tag veranschaulicht.  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 Das folgende Beispiel veranschaulicht die Verwendung des @type\-JSDoc\-Tags.  Wie in diesem Beispiel gezeigt wird, sind einzelne Sternchen \(\*\), die dem anfänglichen Sternchenpaar \(\*\*\) folgen, nicht erforderlich.  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 Im folgenden Beispiel wird die Verwendung des @deprecated\-JSDoc\-Tags veranschaulicht.  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```
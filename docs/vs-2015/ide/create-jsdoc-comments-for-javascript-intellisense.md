---
title: Erstellen von JSDoc-Kommentaren für JavaScript IntelliSense | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 22db62a186c1f1c668a0304a9b586aca85e713c3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758509"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Erstellen von JSDoc-Kommentaren für JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense in Visual Studio zeigt Informationen an, die Sie einem Skript mit standardmäßigen JSDoc-Kommentaren hinzufügen. Sie können JSDoc-Kommentare verwenden, um Informationen zu Codeelementen wie z. B. Funktionen, Felder und Variablen bereitzustellen.  

## <a name="jsdoc-comment-tags"></a>JSDoc-Kommentartags  
 Die folgenden standardmäßigen JSDoc-Kommentartags werden von IntelliSense verwendet, um Informationen zu Ihrem Code anzuzeigen.  


|  JSDoc-Tag   |                       Syntax                        |                                                     Hinweise                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *Beschreibung*              |                                   Gibt eine veraltete Funktion oder Methode an.                                   |
| @description |             @description *Beschreibung*              |                              Gibt die Beschreibung für eine Funktion oder Methode an.                               |
|    @param    | @param {*Typ*} *Parametername*<em>Beschreibung</em> | Gibt Informationen für einen Parameter in einer Funktion oder Methode an.<br /><br /> TypeScript unterstützt auch @paramTag. |
|  @property   |          @property {*Typ*} *Eigenschaftenname*          |   Gibt Informationen an, darunter eine Beschreibung, die entweder für ein Feld oder für einen Member gilt, der über ein Objekt definiert wird.    |
|   @returns   |                  @returns {*Typ*}                  |           Gibt einen Rückgabewert an.<br /><br /> Verwenden Sie für TypeScript, @returnType anstelle von @returns.           |
|   @summary   |               @summary *Beschreibung*                |                   Gibt die Beschreibung einer Funktion oder Methode an (identisch mit @description).                   |
|    @type     |                   @type {*Typ*}                    |                                Gibt den Typ für eine Konstante oder eine Variable an.                                |
|   @typedef   |         @typedef {*Typ*} *Benutzerdefinierter_Typname*          |                                            Gibt einen benutzerdefinierten Typ an.                                            |

### <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung der @description, @param, und @return JSDoc-tags für eine Funktion namens `getArea`.  

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

 ![IntelliSense-Informationen für eine Funktion](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")  

 Das folgende Beispiel zeigt, wie Sie mit der @typedef markieren Sie mit der @property Tag.  

```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  

var w = new Weather();  
```  

 Das folgende Beispiel zeigt die Verwendung der @type JSDoc-Tags. Wie in diesem Beispiel veranschaulicht wird, sind einzelne Sternchen (*), die dem anfänglichen Sternchenpaar (\*\*) folgen, nicht erforderlich.  

```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  

```  

 Das folgende Beispiel zeigt, wie Sie mit der @deprecated JSDoc-Tag.  

```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```

---
title: Erstellen von JSDoc-Kommentaren für JavaScript IntelliSense | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b974f3450b88ab22e58e284881f270c1b3d72298
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619276"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Erstellen von JSDoc-Kommentaren für JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense in Visual Studio zeigt Informationen an, die Sie einem Skript mit standardmäßigen JSDoc-Kommentaren hinzufügen. Sie können JSDoc-Kommentare verwenden, um Informationen zu Codeelementen wie z. B. Funktionen, Felder und Variablen bereitzustellen.

## <a name="jsdoc-comment-tags"></a>JSDoc-Kommentartags
 Die folgenden standardmäßigen JSDoc-Kommentartags werden von IntelliSense verwendet, um Informationen zu Ihrem Code anzuzeigen.

|  JSDoc-Tag   |                       Syntax                        |                                                     Notizen                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *Beschreibung*              |                                   Gibt eine veraltete Funktion oder Methode an.                                   |
| @description |             @description *Beschreibung*              |                              Gibt die Beschreibung für eine Funktion oder Methode an.                               |
|    @param    | @param {*Typ*} *Parametername*<em>Beschreibung</em> | Gibt Informationen für einen Parameter in einer Funktion oder Methode an.<br /><br /> Typescript unterstützt auch @paramTag. |
|  @property   |          @property {*Typ*} *Eigenschaftenname*          |   Gibt Informationen an, darunter eine Beschreibung, die entweder für ein Feld oder für einen Member gilt, der über ein Objekt definiert wird.    |
|   @returns   |                  @returns {*Typ*}                  |           Gibt einen Rückgabewert an.<br /><br /> Verwenden Sie für typescript @returnType anstelle von @returns.           |
|   @summary   |               @summary *Beschreibung*                |                   Gibt die Beschreibung für eine Funktion oder Methode an (identisch mit @description).                   |
|    @type     |                   @type {*Typ*}                    |                                Gibt den Typ für eine Konstante oder eine Variable an.                                |
|   @typedef   |         @typedef {*Typ*} *Benutzerdefinierter_Typname*          |                                            Gibt einen benutzerdefinierten Typ an.                                            |

### <a name="examples"></a>Beispiele
 Das folgende Beispiel zeigt die Verwendung der Tags @description, @param und @return JSDoc für eine Funktion mit dem Namen `getArea`.

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

 Im folgenden Beispiel wird gezeigt, wie das @typedef-Tag mit dem @property-Tag verwendet wird.

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

 Im folgenden Beispiel wird gezeigt, wie das @deprecated JSDoc-Tag verwendet wird.

```javascript
/**
 * @deprecated since version 2.0
 */
function old() {
}
```

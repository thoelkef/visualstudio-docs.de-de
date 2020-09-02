---
title: '&lt;veraltet &gt; (JavaScript) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 343f3ebe4bea7ee999f60741c189f35defb0ac7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665802"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;veraltet &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt eine veraltete Funktion oder Methode an.

## <a name="syntax"></a>Syntax

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>Parameter
 `type` ist optional. Gibt an, ob die Funktion oder Methode in einer zukünftigen Version entfernt wird oder ob die Funktion oder Methode bereits entfernt wurde und ihre Verwendung möglicherweise zu einem Fehler führen wird. Legen Sie es auf `deprecate` fest, um anzugeben, dass die Funktion oder Methode in einer zukünftigen Version entfernt wird. Legen Sie es auf `remove` fest, um anzugeben, dass die Funktion oder Methode bereits entfernt wurde.

 `locid` ist optional. Der Bezeichner für Lokalisierungsinformationen über die Funktion oder Methode. Der Bezeichner ist entweder eine Member-ID, oder er entspricht dem `name`-Attributwert in einem Meldungsbündel, das von OpenAjax-Metadaten definiert wird. Der Bezeichnertyp hängt vom Format ab, das im-Element angegeben ist [\<loc>](../ide/loc-javascript.md) .

 `description` ist optional. Eine Beschreibung der Funktion oder Methode, die veraltet ist.

## <a name="remarks"></a>Bemerkungen
 Die Elemente, die verwendet werden, um Funktionen, wie unter anderem `<deprecated>`, mit Anmerkungen zu versehen und müssen vor allen Anweisungen in den Funktionstext eingefügt werden. Wenn Sie eine Funktion als veraltet markieren, empfiehlt es sich, das zugehörige- [\<summary>](../ide/summary-javascript.md) Element durch das-Element zu ersetzen `<deprecated>` .

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird die Verwendung des `<deprecated>`-Elements veranschaulicht.

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

## <a name="see-also"></a>Weitere Informationen
 [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)

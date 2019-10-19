---
title: '&lt;returns &gt; (JavaScript) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8fd8cdc8acdbf42b97e00f3c85647dd863721d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669954"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt Dokumentationsinformationen für das Ergebnis einer Funktion oder eines Methodenaufrufs an.

## <a name="syntax"></a>Syntax

```
<returns type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID" value="code">description
</returns>
```

#### <a name="parameters"></a>Parameter
 `type` ist optional. Der Datentyp des Rückgabewerts. Als Typ kann eines der folgenden Elemente verwendet werden:

- Ein ECMAScript-Sprachentyp in der ECMAScript 5-Spezifikation, wie `Number` und `Object`

- Ein DOM-Objekt, wie `HTMLElement`, `Window` und `Document`

- Eine JavaScript-Konstruktorfunktion

  `integer` ist optional. Wenn `type` auf `Number` festgelegt ist, wird angegeben, ob der Rückgabewert eine ganze Zahl ist. Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Rückgabewert eine ganze Zahl ist; andernfalls ist es auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `domElement` ist optional. Dieses Attribut ist veraltet; das Attribut `type` hat Vorrang vor diesem Attribut. Dieses Attribut gibt an, ob der dokumentierte Rückgabewert ein DOM-Element ist. Legen Sie es auf `true` fest, um anzugeben, dass der Rückgabewert ein DOM-Element ist; andernfalls ist es auf `false` festzulegen. Wenn das `type`-Attribut nicht festgelegt ist und `domElement` auf `true` festgelegt wurde, behandelt IntelliSense den dokumentierten Rückgabewert bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.

  `mayBeNull` ist optional. Gibt an, ob der dokumentierte Rückgabewert auf NULL festgelegt werden kann. Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Rückgabewert auf NULL festgelegt werden kann; andernfalls ist es auf `false` festzulegen. Der Standardwert ist `false`sein. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `elementType` ist optional. Wenn das `type`-Attribut `Array` lautet, wird der Typ des Elements im Array angegeben.

  `elementInteger` ist optional. Wenn das `type`-Attribut `Array` und das `elementType`-Attribut `Number` lautet, wird angegeben, ob die Elemente im Array ganze Zahlen sind. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array ganze Zahlen sind; andernfalls ist das Attribut auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `elementDomElement` ist optional. Dieses Attribut ist veraltet; das Attribut `elementType` hat Vorrang vor diesem Attribut. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array DOM-Elemente sind. Wenn Sie Attribut auf `true` festlegen, wird angegeben, dass die Elemente DOM-Elemente sind; andernfalls ist das Attribut auf `false` festzulegen. Wenn das `elementType`-Attribut nicht festgelegt ist und `elementDomElement` auf `true` festgelegt wird, behandelt IntelliSense jedes Element im Array bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.

  `elementMayBeNull` ist optional. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array auf NULL festgelegt werden können. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array auf NULL festgelegt werden können; andernfalls ist das Attribut auf `false` festzulegen. Der Standardwert ist `false`sein. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `locid` ist optional. Der Bezeichner für Lokalisierungsinformationen über den Rückgabewert. Der Bezeichner ist entweder eine Member-ID, oder er entspricht dem `name`-Attributwert in einem Meldungsbündel, das von OpenAjax-Metadaten definiert wird. Der Bezeichnertyp hängt vom Format ab, das im Tag [\<loc>](../ide/loc-javascript.md) angegeben wird.

  `value` ist optional. Gibt den Code an, der anstelle des Funktionscodes für die Verwendung mit IntelliSense ausgewertet werden soll. Beispielsweise können Sie dieses Attribut verwenden, um IntelliSense für asynchrone Rückrufe bereitzustellen, wie etwa `Promise`. Durch Verwendung des `value`-Attributs mit dem `<returns>`-Element kann die IntelliSense-Leistung durch Umgehung einer langwierigen Codeausführung verbessert werden.

  `description` ist optional. Eine Beschreibung des Rückgabewerts.

## <a name="remarks"></a>Anmerkungen
 Das `<returns>`-Element muss im Funktionstext vor allen Anweisungen eingefügt werden.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird die Verwendung des Elements `<returns>` veranschaulicht.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// The following examples use the <remarks> element with a value attribute.

function getJson(complete) {
    /// <returns value='complete("")' ></returns>
    var r = new XMLHttpRequest();
    // . . .
}

getJson(function (json) {
    json.  // IntelliSense for a String object is
           // available here.
});

function calculate(x) {
    /// <returns value='1'/>
}
calculate().  // Completion list for a Number.

```

## <a name="see-also"></a>Siehe auch
 [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)

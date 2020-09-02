---
title: '&lt;param &gt; (JavaScript) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca6207d22d82e607fa589f944230b36b46e633c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670359"
---
# <a name="ltparamgt-javascript"></a>&lt;param &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt Dokumentationsinformationen für einen Parameter in einer Funktion oder Methode an.

## <a name="syntax"></a>Syntax

```
<param name="parameterName" type="ParameterType"
    integer="true|false" domElement="true|false"
    mayBeNull="true|false" elementType="ArrayElementType"
    elementInteger="true|false" elementDomElement="true|false"
    elementMayBeNull="true|false" locid="descriptionID"
    parameterArray="true|false" optional="true|false"
    value="code">description
</param>
```

#### <a name="parameters"></a>Parameter
 `name` ist erforderlich. Der Name des Parameters.

 `type` ist optional. Der Datentyp des Parameters. Als Typ kann eines der folgenden Elemente verwendet werden:

- Ein ECMAScript-Sprachentyp in der ECMAScript 5-Spezifikation, wie `Number` und `Object`

- Ein DOM-Objekt, wie `HTMLElement`, `Window` und `Document`

- Eine JavaScript-Konstruktorfunktion

  `integer` ist optional. Wenn `type` auf `Number` festgelegt ist, wird angegeben, ob der Parameter eine ganze Zahl ist. Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Parameter eine ganze Zahl ist; andernfalls ist es auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `domElement` ist optional. Dieses Attribut ist veraltet; das Attribut `type` hat Vorrang vor diesem Attribut. Dieses Attribut gibt an, ob der dokumentierte Parameter ein DOM-Element ist. Legen Sie es auf `true` fest, um anzugeben, dass der Parameter ein DOM-Element ist; andernfalls ist es auf `false` festzulegen. Wenn das `type`-Attribut nicht festgelegt ist und `domElement` auf `true` festgelegt wurde, behandelt IntelliSense den dokumentierten Parameter bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.

  `mayBeNull` ist optional. Gibt an, ob der dokumentierte Parameter auf NULL festgelegt werden kann. Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Parameter auf NULL festgelegt werden kann; andernfalls ist es auf `false` festzulegen. Standardwert: `false`. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `elementType` ist optional. Wenn das `type`-Attribut `Array` lautet, wird der Typ des Elements im Array angegeben.

  `elementInteger` ist optional. Wenn das `type`-Attribut `Array` und das `elementType`-Attribut `Number` lautet, wird angegeben, ob die Elemente im Array ganze Zahlen sind. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array ganze Zahlen sind; andernfalls ist das Attribut auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `elementDomElement` ist optional. Dieses Attribut ist veraltet; das Attribut `elementType` hat Vorrang vor diesem Attribut. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array DOM-Elemente sind. Wenn Sie Attribut auf `true` festlegen, wird angegeben, dass die Elemente DOM-Elemente sind; andernfalls ist das Attribut auf `false` festzulegen. Wenn das `elementType`-Attribut nicht festgelegt ist und `elementDomElement` auf `true` festgelegt wird, behandelt IntelliSense jedes Element im Array bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.

  `elementMayBeNull` ist optional. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array auf NULL festgelegt werden können. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array auf NULL festgelegt werden können; andernfalls ist das Attribut auf `false` festzulegen. Standardwert: `false`. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `locid` ist optional. Der Bezeichner für Lokalisierungsinformationen über den Parameter. Der Bezeichner ist entweder eine Member-ID, oder er entspricht dem `name`-Attributwert in einem Meldungsbündel, das von OpenAjax-Metadaten definiert wird. Der Bezeichnertyp hängt vom Format ab, das im-Element angegeben ist [\<loc>](../ide/loc-javascript.md) .

  `parameterArray` ist optional. Gibt an, ob der dokumentierte Parameter im Funktionsaufruf wiederholt werden kann, ähnlich der Wiederholung von Parametern, die in der `String.format`-Funktion unterstützt werden. Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Parameter wiederholt werden kann; andernfalls ist es auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `optional` ist optional. Gibt an, ob der dokumentierte Parameter in der aufrufenden Funktion optional ist. Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Parameter optional ist; andernfalls ist es auf `false` festzulegen.

  `value` ist optional. Gibt den Code an, der anstelle des Funktionscodes für die Verwendung mit IntelliSense ausgewertet werden soll. Sie können dieses Attribut zur Bereitstellung von Typinformationen verwenden, wenn der Parametertyp nicht definiert ist. Beispielsweise können Sie verwenden, `value=’1’` um den Parametertyp als Zahl zu behandeln.

  `description` ist optional. Eine Beschreibung des Parameters

## <a name="remarks"></a>Bemerkungen
 Das einzig erforderliche Attribut ist das `name`-Attribut. Alle anderen Attribute sind optional.

 Elemente, die verwendet werden, um Funktionen mit Anmerkungen zu versehen, wie z [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) . b., und [\<returns>](../ide/returns-javascript.md) , müssen vor allen Anweisungen im Funktions Rumpf abgelegt werden.

 Wenn es mehrere `<param>`-Elemente gibt, die denselben Namen aufweisen, wird eines der `<param>`-Elemente verwendet, und die redundanten Elemente werden ignoriert. Das Verhalten, das bestimmt, welches Element verwendet wird, ist nicht definiert. Wenn `name` auf einen nicht vorhandenen Parameter verweist, wird das Element ignoriert.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird die Verwendung des Elements `<param>` veranschaulicht.

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

// Uses of <param> with the value attribute.

function calculate(a) {
    /// <param name='a' value='1'/>
    a.    // Completion list for a Number.
}

function calculate(a) {
    /// <param name='a' value='{x:0,y:0}'/>
    a.    // x and y appear in the completion list.
}

```

## <a name="see-also"></a>Weitere Informationen
 [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)

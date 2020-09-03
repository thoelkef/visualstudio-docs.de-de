---
title: '&lt;var&gt; (JavaScript) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f72b403d4c6c9cc71bc2a3fdbff8f778a44b3b55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663060"
---
# <a name="ltvargt-javascript"></a>&lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt Dokumentationsinformationen für eine Variable an.

## <a name="syntax"></a>Syntax

```
<var type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID">description
</var>
```

#### <a name="parameters"></a>Parameter
 `type` ist optional. Der Datentyp der Variablen. Als Typ kann eines der folgenden Elemente verwendet werden:

- Ein ECMAScript-Sprachentyp in der ECMAScript 5-Spezifikation, wie `Number` und `Object`

- Ein DOM-Objekt, wie `HTMLElement`, `Window` und `Document`

- Eine JavaScript-Konstruktorfunktion

  `integer` ist optional. Wenn `type` auf `Number` festgelegt ist, wird angegeben, ob die Variable eine ganze Zahl ist. Legen Sie das Attribut auf `true` fest, um anzugeben, dass die Variable eine ganze Zahl ist; andernfalls ist es auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `domElement` ist optional. Dieses Attribut ist veraltet; das Attribut `type` hat Vorrang vor diesem Attribut. Dieses Attribut gibt an, ob die dokumentierte Variable ein DOM-Element ist. Legen Sie es auf `true` fest, um anzugeben, dass die Variable ein DOM-Element ist; andernfalls ist es auf `false` festzulegen. Wenn das `type`-Attribut nicht festgelegt ist und `domElement` auf `true` festgelegt wurde, behandelt IntelliSense die dokumentierte Variable bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.

  `mayBeNull` ist optional. Gibt an, ob die dokumentierte Variable auf NULL festgelegt werden kann. Legen Sie das Attribut auf `true` fest, um anzugeben, dass die Variable auf NULL festgelegt werden kann; andernfalls ist es auf `false` festzulegen. Standardwert: `false`. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `elementType` ist optional. Wenn das `type`-Attribut `Array` lautet, wird der Typ des Elements im Array angegeben.

  `elementInteger` ist optional. Wenn das `type`-Attribut `Array` und das `elementType`-Attribut `Number` lautet, wird angegeben, ob die Elemente im Array ganze Zahlen sind. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array ganze Zahlen sind; andernfalls ist das Attribut auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `elementDomElement` ist optional. Dieses Attribut ist veraltet; das Attribut `elementType` hat Vorrang vor diesem Attribut. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array DOM-Elemente sind. Wenn Sie Attribut auf `true` festlegen, wird angegeben, dass die Elemente DOM-Elemente sind; andernfalls ist das Attribut auf `false` festzulegen. Wenn das `elementType`-Attribut nicht festgelegt ist und `elementDomElement` auf `true` festgelegt wird, behandelt IntelliSense jedes Element im Array bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.

  `elementMayBeNull` ist optional. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array auf NULL festgelegt werden können. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array auf NULL festgelegt werden können; andernfalls ist das Attribut auf `false` festzulegen. Standardwert: `false`. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `helpKeyword` ist optional. Das Schlüsselwort für die F1-Hilfe.

  `locid` ist optional. Der Bezeichner für Lokalisierungsinformationen über die Variable. Der Bezeichner ist entweder eine Member-ID, oder er entspricht dem `name`-Attributwert in einem Meldungsbündel, das von OpenAjax-Metadaten definiert wird. Der Bezeichnertyp hängt vom Format ab, das im-Tag angegeben ist [\<loc>](../ide/loc-javascript.md) .

  `description` ist optional. Eine Beschreibung der Variable.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird die Verwendung des Elements `<var>` veranschaulicht.

```javascript
/// <var>A rectangle that has a width of 5.</var>
var Rectangle = {
    /// <field type = 'Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type = 'Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}
```

## <a name="see-also"></a>Weitere Informationen
 [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)

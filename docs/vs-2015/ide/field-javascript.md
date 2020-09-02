---
title: '&lt;Field &gt; (JavaScript) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3fc786e4d99d1eaff4a8b152ea9496ce8400ff1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663856"
---
# <a name="ltfieldgt-javascript"></a>&lt;Field &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt Informationen zur Dokumentation an, darunter eine Beschreibung, die entweder für ein Feld oder für einen Member gilt, der über ein Objekt definiert wird.

## <a name="syntax"></a>Syntax

```
<field name="fieldName" static="true|false"
    type="FieldType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID"
    value="code">description
</field>
```

#### <a name="parameters"></a>Parameter
 `name` Der Name des Felds oder des Members. Wenn das Element `<field>` in einer Konstruktorfunktion verwendet wird, ist `name` erforderlich und definiert den Member, für den das Tag gilt. Wenn das Element `<field>` ein Feld direkt kennzeichnet, wird dieses Attribut ignoriert und der von Visual Studio verwendete Name ist der Name des tatsächlichen Felds im Quellcode.

 `static` ist optional. Gibt an, ob das Feld ein Member der Konstruktorfunktion oder des durch die Konstruktorfunktion zurückgegebenen Objekts ist. Wenn dieses Attribut auf `true` festgelegt ist, wird das Feld als Member der Konstruktorfunktion behandelt. Wenn dieses Attribut auf `false` festgelegt ist, wird das Feld als Member des von der Konstruktorfunktion zurückgegebenen Objekts behandelt.

 `type` ist optional. Der Datentyp des Felds. Als Typ kann eines der folgenden Elemente verwendet werden:

- Ein ECMAScript-Sprachentyp in der ECMAScript 5-Spezifikation, wie `Number` und `Object`

- Ein DOM-Objekt, wie `HTMLElement`, `Window` und `Document`

- Eine JavaScript-Konstruktorfunktion

  `integer` ist optional. Wenn `type` auf `Number` festgelegt ist, wird angegeben, ob das Feld eine ganze Zahl ist. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass das Feld eine ganze Zahl ist; andernfalls ist das Attribut auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `domElement` ist optional. Dieses Attribut ist veraltet; das Attribut `type` hat Vorrang vor diesem Attribut. Dieses Attribut gibt an, ob das dokumentierte Feld ein DOM-Element ist. Wenn es auf `true` festgelegt ist, wird angegeben, dass das Feld ein DOM-Element ist; andernfalls ist es auf `false` festzulegen. Wenn `type` nicht festgelegt ist und `domElement` auf `true` festgelegt wurde, behandelt das dokumentierte Feld IntelliSense bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.

  `mayBeNull` ist optional. Gibt an, ob das dokumentierte Feld auf NULL festgelegt werden kann. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass das Feld auf NULL festgelegt werden kann; andernfalls ist das Attribut auf `false` festzulegen. Standardwert: `false`. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `elementType` ist optional. Wenn das `type`-Attribut `Array` lautet, wird der Typ des Elements im Array angegeben.

  `elementInteger` ist optional. Wenn das `type`-Attribut `Array` und das `elementType`-Attribut `Number` lautet, wird angegeben, ob die Elemente im Array ganze Zahlen sind. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array ganze Zahlen sind; andernfalls ist das Attribut auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `elementDomElement` ist optional. Dieses Attribut ist veraltet; das Attribut `elementType` hat Vorrang vor diesem Attribut. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array DOM-Elemente sind. Wenn Sie Attribut auf `true` festlegen, wird angegeben, dass die Elemente DOM-Elemente sind; andernfalls ist das Attribut auf `false` festzulegen. Wenn das `elementType`-Attribut nicht festgelegt ist und `elementDomElement` auf `true` festgelegt wird, behandelt IntelliSense jedes Element im Array bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.

  `elementMayBeNull` ist optional. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array auf NULL festgelegt werden können. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array auf NULL festgelegt werden können; andernfalls ist das Attribut auf `false` festzulegen. Standardwert: `false`. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.

  `helpKeyword` ist optional. Das Schlüsselwort für die F1-Hilfe.

  `locid` ist optional. Der Bezeichner für Lokalisierungsinformationen über das Feld. Der Bezeichner ist entweder eine Member-ID, oder er entspricht dem `name`-Attributwert in einem Meldungsbündel, das von OpenAjax-Metadaten definiert wird. Der Bezeichnertyp hängt vom Format ab, das im-Tag angegeben ist [\<loc>](../ide/loc-javascript.md) .

  `value` ist optional. Gibt den Code an, der anstelle des Funktionscodes für die Verwendung mit IntelliSense ausgewertet werden soll. Für das Element `<field>` wird dieses Attribut in Konstruktorfunktionen unterstützt, jedoch nicht in Objektliteralen. Sie können dieses Attribut zur Bereitstellung von Typinformationen verwenden, wenn der Feldtyp nicht definiert wird. Beispielsweise können Sie verwenden, `value=’1’` um den Feldtyp als Zahl zu behandeln.

  `description` ist optional. Eine Beschreibung des Felds.

## <a name="remarks"></a>Bemerkungen
 Das Attribut `name` ist erforderlich, wenn Sie ein Feld in einer Konstruktorfunktion dokumentieren. In allen anderen Szenarien sind sämtliche Attribute für das Element `<field>` optional.

 Wenn Sie eine Konstruktorfunktion dokumentieren, muss das Element `<field>` direkt vor der Felddeklaration angezeigt werden. Das `name`-Attribut muss mit dem Feldnamen übereinstimmen, der im Quellcode verwendet wird. Für Objektmember kann das `name`-Attribut ausgelassen werden, wenn das Element `<field>` direkt vor der Objektmemberdeklaration angezeigt wird.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird die Verwendung des Elements `<field>` veranschaulicht.

```javascript
// Use of <field> in an object definition.
var Rectangle = {
    /// <field type='Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type='Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}

// Use of <field> in a constructor function.
// The name attribute is required.
function Engine() {
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
    this.HorsePower = 150;
}
```

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Verwendung des Elements `<field>` mit dem Attribut `static` veranschaulicht, das auf `true` festgelegt ist.

```javascript
function Engine() {
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>
}

Engine.HorsePower = 140;
// IntelliSense on the field is available here.
Engine.

```

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Verwendung des Elements `<field>` mit dem Attribut `static` veranschaulicht, das auf `false` festgelegt ist.

```javascript
function Engine() {
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>
}

Engine.HorsePower = 140;
var eng = new Engine();
// IntelliSense on the field is available here.
eng.

```

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Verwendung des Elements `<field>` mit dem Attribut `value` veranschaulicht.

```javascript
function calculator(a) {
    /// <field name='f' value='1'/>
}
new calculator().f.   // Completion list for a Number.

```

## <a name="see-also"></a>Weitere Informationen
 [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)

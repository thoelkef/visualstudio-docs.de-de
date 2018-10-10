---
title: '&lt;Gibt&gt; (JavaScript) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 733fa3706eb7c8eeef6a8e8243eaeeac6d1b0f78
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879727"
---
# <a name="ltreturnsgt-javascript"></a>&lt;Gibt&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Dokumentation zu Visual Studio 2017](/visualstudio/).  
  
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
 `type`  
 Dies ist optional. Der Datentyp des Rückgabewerts. Als Typ kann eines der folgenden Elemente verwendet werden:  
  
-   Ein ECMAScript-Sprachentyp in der ECMAScript 5-Spezifikation, wie `Number` und `Object`  
  
-   Ein DOM-Objekt, wie `HTMLElement`, `Window` und `Document`  
  
-   Eine JavaScript-Konstruktorfunktion  
  
 `integer`  
 Dies ist optional. Wenn `type` auf `Number` festgelegt ist, wird angegeben, ob der Rückgabewert eine ganze Zahl ist. Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Rückgabewert eine ganze Zahl ist; andernfalls ist es auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.  
  
 `domElement`  
 Dies ist optional. Dieses Attribut ist veraltet; das Attribut `type` hat Vorrang vor diesem Attribut. Dieses Attribut gibt an, ob der dokumentierte Rückgabewert ein DOM-Element ist. Legen Sie es auf `true` fest, um anzugeben, dass der Rückgabewert ein DOM-Element ist; andernfalls ist es auf `false` festzulegen. Wenn das `type`-Attribut nicht festgelegt ist und `domElement` auf `true` festgelegt wurde, behandelt IntelliSense den dokumentierten Rückgabewert bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.  
  
 `mayBeNull`  
 Dies ist optional. Gibt an, ob der dokumentierte Rückgabewert auf NULL festgelegt werden kann. Legen Sie das Attribut auf `true` fest, um anzugeben, dass der Rückgabewert auf NULL festgelegt werden kann; andernfalls ist es auf `false` festzulegen. Der Standardwert ist `false`. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.  
  
 `elementType`  
 Dies ist optional. Wenn das `type`-Attribut `Array` lautet, wird der Typ des Elements im Array angegeben.  
  
 `elementInteger`  
 Dies ist optional. Wenn das `type`-Attribut `Array` und das `elementType`-Attribut `Number` lautet, wird angegeben, ob die Elemente im Array ganze Zahlen sind. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array ganze Zahlen sind; andernfalls ist das Attribut auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.  
  
 `elementDomElement`  
 Dies ist optional. Dieses Attribut ist veraltet; das Attribut `elementType` hat Vorrang vor diesem Attribut. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array DOM-Elemente sind. Wenn Sie Attribut auf `true` festlegen, wird angegeben, dass die Elemente DOM-Elemente sind; andernfalls ist das Attribut auf `false` festzulegen. Wenn das `elementType`-Attribut nicht festgelegt ist und `elementDomElement` auf `true` festgelegt wird, behandelt IntelliSense jedes Element im Array bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.  
  
 `elementMayBeNull`  
 Dies ist optional. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array auf NULL festgelegt werden können. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array auf NULL festgelegt werden können; andernfalls ist das Attribut auf `false` festzulegen. Der Standardwert ist `false`. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.  
  
 `locid`  
 Dies ist optional. Der Bezeichner für Lokalisierungsinformationen über den Rückgabewert. Der Bezeichner ist entweder eine Member-ID, oder er entspricht dem `name`-Attributwert in einem Meldungsbündel, das von OpenAjax-Metadaten definiert wird. Der Bezeichnertyp hängt von dem angegebenen Format in die [ \<Loc >](../ide/loc-javascript.md) Tag.  
  
 `value`  
 Dies ist optional. Gibt den Code an, der anstelle des Funktionscodes für die Verwendung mit IntelliSense ausgewertet werden soll. Beispielsweise können Sie dieses Attribut verwenden, um IntelliSense für asynchrone Rückrufe bereitzustellen, wie etwa `Promise`. Durch Verwendung des `value`-Attributs mit dem `<returns>`-Element kann die IntelliSense-Leistung durch Umgehung einer langwierigen Codeausführung verbessert werden.  
  
 `description`  
 Dies ist optional. Eine Beschreibung des Rückgabewerts.  
  
## <a name="remarks"></a>Hinweise  
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




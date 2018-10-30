---
title: '&lt;Wert&gt; (JavaScript) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f88f3ae2e7442549004d2331b4517eb7fa2b5509
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914332"
---
# <a name="ltvaluegt-javascript"></a>&lt;Wert&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt Dokumentationsinformationen für `get`- und `set`-Funktionen für ECMAScript 3-Eigenschaften an.  
  
## <a name="syntax"></a>Syntax  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### <a name="parameters"></a>Parameter  
 `type`  
 Dies ist optional. Der Datentyp der Eigenschaft. Als Typ kann eines der folgenden Elemente verwendet werden:  
  
- Ein ECMAScript-Sprachentyp in der ECMAScript 5-Spezifikation, wie `Number` und `Object`  
  
- Ein DOM-Objekt, wie `HTMLElement`, `Window` und `Document`  
  
- Eine JavaScript-Konstruktorfunktion  
  
  `integer`  
  Dies ist optional. Wenn `type` auf `Number` festgelegt ist, wird angegeben, ob die Eigenschaft eine ganze Zahl ist. Legen Sie das Attribut auf `true` fest, um anzugeben, dass die Eigenschaft eine ganze Zahl ist; andernfalls ist es auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.  
  
  `domElement`  
  Dies ist optional. Dieses Attribut ist veraltet; das Attribut `type` hat Vorrang vor diesem Attribut. Dieses Attribut gibt an, ob die dokumentierte Eigenschaft ein DOM-Element ist. Legen Sie es auf `true` fest, um anzugeben, dass die Eigenschaft ein DOM-Element ist; andernfalls ist es auf `false` festzulegen. Wenn das `type`-Attribut nicht festgelegt ist und `domElement` auf `true` festgelegt wurde, behandelt IntelliSense die dokumentierte Eigenschaft bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.  
  
  `mayBeNull`  
  Dies ist optional. Gibt an, ob die dokumentierte Eigenschaft auf NULL festgelegt werden kann. Legen Sie das Attribut auf `true` fest, um anzugeben, dass die Eigenschaft auf NULL festgelegt werden kann; andernfalls ist es auf `false` festzulegen. Der Standardwert ist `false`. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.  
  
  `elementType`  
  Dies ist optional. Wenn das `type`-Attribut `Array` lautet, wird der Typ des Elements im Array angegeben.  
  
  `elementInteger`  
  Dies ist optional. Wenn das `type`-Attribut `Array` und das `elementType`-Attribut `Number` lautet, wird angegeben, ob die Elemente im Array ganze Zahlen sind. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array ganze Zahlen sind; andernfalls ist das Attribut auf `false` festzulegen. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.  
  
  `elementDomElement`  
  Dies ist optional. Dieses Attribut ist veraltet; das Attribut `elementType` hat Vorrang vor diesem Attribut. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array DOM-Elemente sind. Wenn Sie Attribut auf `true` festlegen, wird angegeben, dass die Elemente DOM-Elemente sind; andernfalls ist das Attribut auf `false` festzulegen. Wenn das `elementType`-Attribut nicht festgelegt ist und `elementDomElement` auf `true` festgelegt wird, behandelt IntelliSense jedes Element im Array bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.  
  
  `elementMayBeNull`  
  Dies ist optional. Wenn das `type`-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array auf NULL festgelegt werden können. Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array auf NULL festgelegt werden können; andernfalls ist das Attribut auf `false` festzulegen. Der Standardwert ist `false`. Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense-Informationen bereitzustellen.  
  
  `locid`  
  Dies ist optional. Der Bezeichner für Lokalisierungsinformationen über die Eigenschaft. Der Bezeichner ist entweder eine Member-ID, oder er entspricht dem `name`-Attributwert in einem Meldungsbündel, das von OpenAjax-Metadaten definiert wird. Der Bezeichnertyp hängt von dem angegebenen Format in die [ \<Loc >](../ide/loc-javascript.md) Element.  
  
  `description`  
  Dies ist optional. Eine Beschreibung der Eigenschaft.  
  
## <a name="remarks"></a>Hinweise  
 ECMAScript 5-Eigenschaften verwenden die [ \<summary >](../ide/summary-javascript.md) Element.  
  
 Verwenden Sie das `<value>`-Element direkt vor der `get`- oder `set`-Funktion.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die Verwendung des `<value>`-Elements in einer `get`-Funktion veranschaulicht.  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)




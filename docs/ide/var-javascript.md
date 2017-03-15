---
title: "&lt;var&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<var>-JavaScript-XML-Tag"
  - "var-JavaScript-XML-Tag"
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt Dokumentationsinformationen für eine Variable an.  
  
## Syntax  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>  
  
```  
  
#### Parameter  
 `type`  
 Optional.  Der Datentyp der Variable.  Als Typ kann eines der folgenden Elemente verwendet werden:  
  
-   Ein ECMAScript\-Sprachentyp in der ECMAScript 5\-Spezifikation, wie `Number` und `Object`  
  
-   Ein DOM\-Objekt, wie `HTMLElement`, `Window` und `Document`  
  
-   Eine JavaScript\-Konstruktorfunktion  
  
 `integer`  
 Optional.  Wenn `type` auf `Number` festgelegt ist, wird angegeben, ob die Variable eine ganze Zahl ist.  Legen Sie das Attribut auf `true` fest, um anzugeben, dass die Variable eine ganze Zahl ist; andernfalls ist es auf `false` festzulegen.  Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense\-Informationen bereitzustellen.  
  
 `domElement`  
 Optional.  Dieses Attribut ist veraltet; das Attribut `type` hat Vorrang vor diesem Attribut.  Dieses Attribut gibt an, ob die dokumentierte Variable ein DOM\-Element ist.  Legen Sie es auf `true` fest, um anzugeben, dass die Variable ein DOM\-Element ist; andernfalls ist es auf `false` festzulegen.  Wenn das `type`\-Attribut nicht festgelegt ist und `domElement` auf `true` festgelegt wurde, behandelt IntelliSense die dokumentierte Variable bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.  
  
 `mayBeNull`  
 Optional.  Gibt an, ob die dokumentierte Variable auf NULL festgelegt werden kann.  Legen Sie das Attribut auf `true` fest, um anzugeben, dass die Variable auf NULL festgelegt werden kann; andernfalls ist es auf `false` festzulegen.  Der Standardwert ist `false`.  Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense\-Informationen bereitzustellen.  
  
 `elementType`  
 Optional.  Wenn das `type`\-Attribut `Array` lautet, wird der Typ des Elements im Array angegeben.  
  
 `elementInteger`  
 Optional.  Wenn das `type`\-Attribut `Array` und das `elementType`\-Attribut `Number` lautet, wird angegeben, ob die Elemente im Array ganze Zahlen sind.  Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array ganze Zahlen sind; andernfalls ist das Attribut auf `false` festzulegen.  Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense\-Informationen bereitzustellen.  
  
 `elementDomElement`  
 Optional.  Dieses Attribut ist veraltet; das Attribut `elementType` hat Vorrang vor diesem Attribut.  Wenn das `type`\-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array DOM\-Elemente sind.  Wenn Sie Attribut auf `true` festlegen, wird angegeben, dass die Elemente DOM\-Elemente sind; andernfalls ist das Attribut auf `false` festzulegen.  Wenn das `elementType`\-Attribut nicht festgelegt ist und `elementDomElement` auf `true` festgelegt wird, behandelt IntelliSense jedes Element im Array bei Ausführung einer Anweisungsvervollständigung als `HTMLElement`.  
  
 `elementMayBeNull`  
 Optional.  Wenn das `type`\-Attribut `Array` lautet, wird angegeben, ob die Elemente im Array auf NULL festgelegt werden können.  Wenn Sie das Attribut auf `true` festlegen, wird angegeben, dass die Elemente im Array auf NULL festgelegt werden können; andernfalls ist das Attribut auf `false` festzulegen.  Der Standardwert ist `false`.  Dieses Attribut wird von nicht Visual Studio verwendet, um IntelliSense\-Informationen bereitzustellen.  
  
 `helpKeyword`  
 Optional.  Das Schlüsselwort für die F1\-Hilfe.  
  
 `locid`  
 Optional.  Der Bezeichner für Lokalisierungsinformationen über die Variable.  Der Bezeichner ist entweder eine Member\-ID, oder er entspricht dem `name`\-Attributwert in einem Meldungsbündel, das von OpenAjax\-Metadaten definiert wird.  Der Bezeichnertyp hängt vom Format ab, das im Tag [\<loc\>](../ide/loc-javascript.md) angegeben wird.  
  
 `description`  
 Optional.  Eine Beschreibung der Variable.  
  
## Beispiel  
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
  
## Siehe auch  
 [XML\-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)
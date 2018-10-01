---
title: '&lt;Signatur&gt; (JavaScript) | Microsoft-Dokumentation'
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
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5b6172609b68e1800dd71b9367d93a52596e88cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509006"
---
# <a name="ltsignaturegt-javascript"></a>&lt;Signatur&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Dokumentation zu Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Gruppiert einen Satz zugehöriger Elementen für eine Funktion oder Methode, um eine Dokumentation für überladene Funktionen bereitzustellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
<signature externalid="id" externalFile="filename"  
    helpKeyword="keyword" locid="descriptionID">  
</signature>   
```  
  
#### <a name="parameters"></a>Parameter  
 `externalid`  
 Dies ist optional. Wenn die `format` -Attribut für die [ \<Loc >](../ide/loc-javascript.md) Element `vsdoc`, dieses Attribut gibt an, das Element-ID verwendet, um den XML-Code zu suchen, die mit der Signatur zugeordnet ist. Anders als das `locid`-Attribut gibt dieses Attribut an, dass alle Elemente im Member, der diese ID aufweist, geladen werden sollen. Alle zugeordneten Beschreibungsinformationen, die im XML-Code vorhanden sind, werden auch mit den Elementen zusammengeführt, die in der Signatur angegeben sind. Dies ermöglicht es Ihnen, zusätzliche Elemente, wie `<capability>`, in der Sidecardatei anzugeben, ohne sie in der Quelldatei anzugeben. `externalid` ist ein optionales Attribut.  
  
 `externalFile`  
 Dies ist optional. Gibt den Namen der Datei an, in der `externalid` zu finden ist. Dieses Attribut wird ignoriert, wenn kein `externalid` vorhanden ist. Dies ist ein optionales Attribut. Der Standardwert ist der Name der aktuellen Datei, jedoch mit einer XML-Erweiterung anstelle von JS. Standardmäßig werden Suchregeln für verwaltete Ressourcen für die Lokalisierung verwendet, um die Datei zu suchen.  
  
 `helpKeyword`  
 Dies ist optional. Das Schlüsselwort für die F1-Hilfe.  
  
 `locid`  
 Dies ist optional. Der Bezeichner für Lokalisierungsinformationen über das Feld. Der Bezeichner ist entweder eine Member-ID, oder er entspricht dem `name`-Attributwert in einem Meldungsbündel, das von OpenAjax-Metadaten definiert wird. Der Bezeichnertyp hängt von dem angegebenen Format in die [ \<Loc >](../ide/loc-javascript.md) Tag.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie ein `<signature>`-Element für jede der überladenen Funktionsbeschreibung in der JS-Datei, oder verwenden Sie ein `<signature>`-Element für jede angegebene externe Member-ID.  
  
 Das `<signature>`-Element muss im Funktionstext vor allen Anweisungen eingefügt werden. Bei Verwendung [ \<summary >](../ide/summary-javascript.md), [ \<Param >](../ide/param-javascript.md), oder [ \<gibt >](../ide/returns-javascript.md) Elemente mit den `<signature>` Element Platzieren Sie die anderen Elemente innerhalb der `<signature>` Block.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die Verwendung des Elements `<signature>` veranschaulicht.  
  
```javascript  
// Use of <signature> with externalid.  
// Requires use of the <loc> tag to identify the external functions.  
function illuminate(light) {  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />  
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>  
    ///   <param name='light' type='Number' />  
    /// </signature>  
}  
  
// Use of <signature> for overloads implemented in JavaScript.  
function add(a, b) {  
    /// <signature>  
    /// <summary>function summary 1</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 2 – differ by number of params</summary>  
    /// <param name="a" type="Number">Only 1 parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 3 – differ by parameter type</summary>  
    /// <param name="a" type="Number">Number parameter</param>  
    /// <param name="b" type="String">String parameter</param>  
    /// <returns type="Number" />  
    /// </signature>  
    /// <signature>  
    /// <summary>function summary 4 – differ by return type</summary>  
    /// <param name="a" type="Number">The first number</param>  
    /// <param name="b" type="Number">The second number</param>  
    /// <returns type="String" />  
    /// </signature>  
  
    return a + b;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)




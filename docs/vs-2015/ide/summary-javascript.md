---
title: '&lt;Zusammenfassung&gt; (JavaScript) | Microsoft-Dokumentation'
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
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f6b4808112e746e30f0e40d4626f546c3f99b193
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879017"
---
# <a name="ltsummarygt-javascript"></a>&lt;Zusammenfassung&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Dokumentation zu Visual Studio 2017](/visualstudio/).  
  
Gibt die Beschreibung für eine Funktion oder Methode an.  
  
## <a name="syntax"></a>Syntax  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### <a name="parameters"></a>Parameter  
 `locid`  
 Dies ist optional. Der Bezeichner für Lokalisierungsinformationen über die Funktion oder Methode. Der Bezeichner ist entweder eine Member-ID, oder er entspricht dem `name`-Attributwert in einem Meldungsbündel, das von OpenAjax-Metadaten definiert wird. Der Bezeichnertyp hängt von dem angegebenen Format in die [ \<Loc >](../ide/loc-javascript.md) Element.  
  
 `description`  
 Dies ist optional. Eine Beschreibung der Funktion oder Methode.  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente verwendet, um Funktionen, mit Anmerkungen versehen, darunter [ \<summary >](../ide/summary-javascript.md), [ \<Param >](../ide/param-javascript.md), und [ \<gibt >](../ide/returns-javascript.md), muss im Funktionstext vor allen Anweisungen platziert werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die Verwendung des `<summary>`-Elements veranschaulicht.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)




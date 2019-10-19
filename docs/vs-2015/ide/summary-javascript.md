---
title: '&lt;summary&gt; (JavaScript) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f283c2c1825c4b8b02fb5b044ce113231a919317
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646851"
---
# <a name="ltsummarygt-javascript"></a>&lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt die Beschreibung für eine Funktion oder Methode an.

## <a name="syntax"></a>Syntax

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>Parameter
 `locid` ist optional. Der Bezeichner für Lokalisierungsinformationen über die Funktion oder Methode. Der Bezeichner ist entweder eine Member-ID, oder er entspricht dem `name`-Attributwert in einem Meldungsbündel, das von OpenAjax-Metadaten definiert wird. Der Bezeichnertyp hängt vom Format ab, das im Element [\<loc>](../ide/loc-javascript.md) angegeben wird.

 `description` ist optional. Eine Beschreibung der Funktion oder Methode.

## <a name="remarks"></a>Anmerkungen
 Die Elemente, die verwendet werden, um Funktionen, wie unter anderem [\<summary>](../ide/summary-javascript.md), [\<param>](../ide/param-javascript.md) und [\<returns>](../ide/returns-javascript.md), mit Anmerkungen zu versehen und müssen vor allen Anweisungen in den Funktionstext eingefügt werden.

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

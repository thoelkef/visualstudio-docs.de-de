---
title: Name-Eigenschaft (Fehler) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- name
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Name property
- name property, error name
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a12157b4c467499fab23f7c4cb1be91e9ac5440
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640850"
---
# <a name="name-property-error-javascript"></a>name-Eigenschaft (Fehler) (JavaScript)
Gibt den Namen eines Fehlers zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
errorObj.  
name  
  
```  
  
## <a name="parameters"></a>Parameter  
 `errorObj`  
 Erforderlich. Instanz des `Error` Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Namen** -Eigenschaft gibt den Namen oder die Ausnahme einen Fehler zurück. Wenn ein Laufzeitfehler auftritt, wird die Name-Eigenschaft auf einen der folgenden systemeigenen Ausnahme-Typen festgelegt:  
  
|Ausnahmetyp|Bedeutung|  
|--------------------|-------------|  
|ConversionError|Dieser Fehler tritt auf, wenn der Versuch, ein Objekt in etwas zu konvertieren, die konvertiert werden kann.|  
|RangeError|Dieser Fehler tritt auf, wenn eine Funktion mit einem Argument angegeben wird, die den zulässigen Bereich überschritten hat. Angenommen, dieser Fehler tritt auf, wenn Sie versuchen, Sie erstellen ein `Array` Objekt mit einer Länge, die nicht auf eine gültige positive ganze Zahl ist.|  
|ReferenceError|Dieser Fehler tritt auf, wenn ein ungültiger Verweis erkannt wurde. Dieser Fehler wird z. B. auftreten, ist ein erwarteter Verweis `null`.|  
|RegExpError|Dieser Fehler tritt auf, wenn mit einem regulären Ausdruck ein Kompilierungsfehler auftritt. Sobald der reguläre Ausdruck kompiliert ist, kann nicht allerdings dieser Fehler auftreten. In diesem Beispiel wird z. B. auftreten, wenn ein regulärer Ausdruck mit einem Muster, die eine ungültige Syntax aufweist deklariert wird, oder flags außer **ich**, **g**, oder **m**, oder er enthält das gleiche Flag mehr als einmal.|  
|SyntaxError|Dieser Fehler tritt auf, wenn Quelltext analysiert wird und dieser Quelltext nicht die richtige Syntax befolgt. Dieser Fehler wird z. B. auftreten, wenn die `eval` Funktion wird aufgerufen, mit der ein Argument, das kein gültiger Programmtext ist.|  
|TypeError|Dieser Fehler tritt auf, wenn der tatsächliche Typ des Operanden nicht mit den erwarteten Typ übereinstimmt. Ein Beispiel für das Auftreten dieses Fehlers ist ein Funktionsaufruf von etwas, das ist kein Objekt oder den Aufruf nicht unterstützt.|  
|URIError|Dieser Fehler tritt auf, wenn ein ungültiger Uniform Resource Indicator (URI) erkannt wird. Dies ist z. B. Fehler tritt auf, wenn ein unzulässiges Zeichen in eine Zeichenfolge, gefunden wird, codiert oder decodiert.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel bewirkt, dass eine TypeError-Ausnahme ausgelöst wird, und zeigt den Namen des Fehlers und der Meldung.  
  
```JavaScript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>Beispiel  
 Die Ausgabe dieses Codes lautet wie folgt.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Gilt für**: [-Fehlerobjekt.](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description-Eigenschaft (Fehler)](../../javascript/reference/description-property-error-javascript.md)   
 [Message-Eigenschaft (Fehler)](../../javascript/reference/message-property-error-javascript.md)   
 [number-Eigenschaft (Fehler)](../../javascript/reference/number-property-error-javascript.md)
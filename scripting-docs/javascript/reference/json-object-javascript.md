---
title: JSON-Objekt (JavaScript) | Microsoft Docs
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
- JSON
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JSON object
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 43
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5310132368f665c6734c469a67636d33a08858d4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638050"
---
# <a name="json-object-javascript"></a>JSON-Objekt (JavaScript)
Ein systeminternes Objekt, das Funktionen zum Konvertieren von [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Werten in das und aus dem JSON-Format (JavaScript Objekt Notation) bereitstellt. Die `JSON.stringify`-Funktion serialisiert einen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Wert in JSON-Text. Die `JSON.parse`-Funktion deserialisiert JSON-Text, um einen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Wert zu erzeugen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
JSON.[method]  
  
```  
  
## <a name="parameters"></a>Parameter  
 `Method`  
 Erforderlich. Name einer der Methoden des `JSON`-Objekts.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe des `JSON`-Operators kann kein `new`-Objekt erstellt werden. In diesem Fall tritt ein Fehler auf. Sie können das `JSON`-Objekt jedoch überschreiben oder ändern.  
  
 Wenn das Skriptmodul geladen ist, erstellt es das `JSON`-Objekt. Seine Methoden sind jederzeit für das Skript verfügbar.  
  
 Wenn Sie das systeminterne `JSON`-Objekt verwenden möchten, vergewissern Sie sich, dass Sie es nicht mit einem anderen, im Script definierten `JSON`-Objekt überschreiben. Möglicherweise müssen Sie vorhandene Skriptanweisungen ändern, die das Vorhandensein eines `JSON`-Objekts erkennen, da sich die Auswertungen dieser Anweisungen unterscheiden. Dies wird im folgenden Beispiel dargestellt.  
  
```JavaScript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 Im vorherigen Beispiel wird `!this.JSON` in [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)] als "false" ausgewertet. Daher wird der Code in der `if`-Anweisung nicht ausgeführt.  
  
## <a name="functions"></a>Funktionen  
 [JSON.parse-Funktion](../../javascript/reference/json-parse-function-javascript.md)  
  
 [JSON.stringify-Funktion](../../javascript/reference/json-stringify-function-javascript.md)  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ToJSON-Methode (Datum)](../../javascript/reference/tojson-method-date-javascript.md)   
 [JavaScript-Objekte](../../javascript/reference/javascript-objects.md)   
 [Beispiel-app für Hub (Windows Store)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)
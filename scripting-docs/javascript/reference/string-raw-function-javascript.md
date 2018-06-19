---
title: String.Raw-Funktion (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53df2bf0e455da8b1ccc6de3cbf3f4e3ebee4c09
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640160"
---
# <a name="stringraw-function-javascript"></a>String.raw-Funktion (JavaScript)
Gibt eine Vorlagenzeichenfolge in Form einer unformatierten Zeichenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### <a name="parameters"></a>Parameter  
 `templateStr`  
 Erforderlich. Die Vorlagenzeichenfolge.  
  
 `obj`  
 Erforderlich. Ein wohlgeformtes mit der Objektliteralnotation angegebenes Objekt, wie z. B. {raw: 'Wert'}.  
  
 `...substitutions`  
 Dies ist optional. Ein Array (eine [rest-Parameter](../../javascript/functions-javascript.md)) aus einem oder mehreren Ersetzungswerten besteht.  
  
## <a name="remarks"></a>Hinweise  
 Die `String.raw` Funktion dient zur Verwendung mit [Zeichenfolgen für Dokumentvorlagen](../../javascript/advanced/template-strings-javascript.md). Die unformatierte Zeichenfolge enthält alle Escapezeichen und umgekehrten Schrägstriche, die in der Zeichenfolge vorhanden sind.  
  
 Ein Fehler wird ausgelöst, wenn `obj` kein wohlgeformtes Objekt ist.  
  
## <a name="example"></a>Beispiel  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd   
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
---
title: Enumerator-Objekt (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Enumerator
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Enumerator object
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50b1ebfb6e24ed734f008b3c05f10a1687c4aff5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="enumerator-object-javascript"></a>Enumerator-Objekt (JavaScript)
Ermöglicht das Aufzählen der Elemente in einer Auflistung.  
  
> [!WARNING]
>  Dieses Objekt wird nur in Internet Explorer unterstützt, nicht in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -Apps.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## <a name="parameters"></a>Parameter  
 `enumObj`  
 Erforderlich. Der Variablenname, dem das `Enumerator` -Objekt zugewiesen wird.  
  
 `collection`  
 Optional. Ein beliebiges Sammlungsobjekt  
  
## <a name="remarks"></a>Hinweise  
 Sammlungen unterscheiden sich von Arrays darin, dass auf Mitglieder einer Sammlung nicht direkt zugegriffen werden kann. Anstatt wie bei Arrays Indizes zu verwenden, können Sie den Zeiger für das aktuelle Element nur auf das erste oder nächste Element einer Sammlung verschieben.  
  
 Das `Enumerator` -Objekt bietet eine Möglichkeit zum Zugriff auf jedes Mitglied einer Sammlung und verhält sich ähnlich wie die `For...Each` -Anweisung in VBScript.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zeigt die Verwendung des `Enumerator` -Objekts:  
  
```JavaScript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## <a name="properties"></a>Eigenschaften  
 Das `Enumerator` -Objekt hat keine Eigenschaften.  
  
## <a name="methods"></a>Methoden  
 [AtEnd-Methode](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [item-Methode](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [MoveFirst-Methode](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [MoveNext-Methode](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## <a name="requirements"></a>Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6-Standardmodus, Internet Explorer 7-Standardmodus, Internet Explorer 8-Standardmodus, Internet Explorer 9-Standardmodus und Internet Explorer 10-Standardmodus. Wird in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] -Apps nicht unterstützt. Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Boolean-Objekt](../../javascript/reference/boolean-object-javascript.md)
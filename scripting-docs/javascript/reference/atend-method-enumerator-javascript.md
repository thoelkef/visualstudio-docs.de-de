---
title: "atEnd-Methode (Enumerator) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "atEnd"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "atEnd-Methode"
ms.assetid: 326808fb-9a0f-428e-aff1-b11b237913f1
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# atEnd-Methode (Enumerator) (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob sich der Enumerator am Ende der Auflistung befindet  
  
> [!WARNING]
>  Dieses Objekt wird nur in Internet Explorer unterstützt.  
  
## Syntax  
  
```  
  
myEnum.atEnd()  
```  
  
## Hinweise  
 Der erforderliche *myEnum*\-Verweis ist ein beliebiges `Enumerator`\-Objekt.  
  
 Die `atEnd`\-Methode gibt **TRUE** zurück, wenn das aktuelle Element das letzte in der Auflistung ist, die Auflistung leer ist oder das aktuelle Element nicht definiert ist. Andernfalls wird **false** zurückgegeben.  
  
## Beispiel  
 Im folgenden Code wird die `atEnd`\-Methode verwendet, um zu bestimmen, ob das Ende einer Liste von Laufwerken erreicht wurde:  
  
```javascript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6\-Standardmodus, Internet Explorer 7\-Standardmodus, Internet Explorer 8\-Standardmodus, Internet Explorer 9\-Standardmodus und Internet Explorer 10\-Standardmodus. Wird in [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-Apps nicht unterstützt. Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
 **Gilt für**: [Enumeratorobjekt](../../javascript/reference/enumerator-object-javascript.md)  
  
## Siehe auch  
 [item\-Methode \(Enumerator\)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveFirst\-Methode \(Enumerator\)](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [moveNext\-Methode \(Enumerator\)](../../javascript/reference/movenext-method-enumerator-javascript.md)   
 [Enumeratorobjekt](../../javascript/reference/enumerator-object-javascript.md)
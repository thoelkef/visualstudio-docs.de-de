---
title: "moveNext-Methode (Enumerator) (JavaScript) | Microsoft Docs"
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
  - "moveNext"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "MoveNext-Methode"
ms.assetid: 59aa339b-f375-450a-8276-37896a55a824
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# moveNext-Methode (Enumerator) (JavaScript)
Verschiebt das aktuelle Element zum nächsten Element in der Auflistung  
  
> [!WARNING]
>  Dieses Objekt wird nur in Internet Explorer unterstützt.  
  
## Syntax  
  
```  
  
enumObj.moveNext( )   
```  
  
## Hinweise  
 Der erforderliche *enumObj*\-Verweis ist ein beliebiges `Enumerator`\-Objekt.  
  
 Wenn sich der Enumerator am Ende der Auflistung befindet oder die Auflistung leer ist, wird das aktuelle Element auf „undefined“ gesetzt.  
  
## Beispiel  
 Im folgenden Beispiel wird die **moveNext**\-Methode zum Verschieben auf das nächste Laufwerk in der `Drives`\-Auflistung verwendet:  
  
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
 [atEnd\-Methode \(Enumerator\)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [item\-Methode \(Enumerator\)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveFirst\-Methode \(Enumerator\)](../../javascript/reference/movefirst-method-enumerator-javascript.md)
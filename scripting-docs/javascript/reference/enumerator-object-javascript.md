---
title: "Enumerator-Objekt (JavaScript) | Microsoft Docs"
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
  - "Enumerator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Enumerator-Objekt"
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Enumerator-Objekt (JavaScript)
Ermöglicht das Aufzählen der Elemente in einer Auflistung.  
  
> [!WARNING]
>  Dieses Objekt wird nur in Internet Explorer unterstützt, nicht in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps.  
  
## Syntax  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## Parameter  
 `enumObj`  
 Erforderlich. Der Variablenname, dem das `Enumerator`\-Objekt zugewiesen wird.  
  
 `collection`  
 Optional. Ein beliebiges Sammlungsobjekt  
  
## Hinweise  
 Sammlungen unterscheiden sich von Arrays darin, dass auf Mitglieder einer Sammlung nicht direkt zugegriffen werden kann. Anstatt wie bei Arrays Indizes zu verwenden, können Sie den Zeiger für das aktuelle Element nur auf das erste oder nächste Element einer Sammlung verschieben.  
  
 Das `Enumerator`\-Objekt bietet eine Möglichkeit zum Zugriff auf jedes Mitglied einer Sammlung und verhält sich ähnlich wie die `For...Each`\-Anweisung in VBScript.  
  
## Beispiel  
 Der folgende Code zeigt die Verwendung des `Enumerator`\-Objekts:  
  
```javascript  
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
  
## Eigenschaften  
 Das `Enumerator`\-Objekt hat keine Eigenschaften.  
  
## Methoden  
 [atEnd\-Methode](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [item\-Methode](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [moveFirst\-Methode](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [moveNext\-Methode](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6\-Standardmodus, Internet Explorer 7\-Standardmodus, Internet Explorer 8\-Standardmodus, Internet Explorer 9\-Standardmodus und Internet Explorer 10\-Standardmodus. Wird in [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]\-Apps nicht unterstützt. Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
## Siehe auch  
 [Boolean\-Objekt](../../javascript/reference/boolean-object-javascript.md)
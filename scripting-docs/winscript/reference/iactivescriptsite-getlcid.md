---
title: "IActiveScriptSite::GetLCID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetLCID"
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetLCID
Ruft den Gebietsschemabezeichner ab, der der Benutzeroberfläche des Hosts zugeordnet ist.  Das Skriptmodul verwendet den Bezeichner, um sicherzustellen, dass die Fehlerzeichenfolgen und andere Elemente, die vom Modul generiert werden, in der entsprechenden Sprache angezeigt.  
  
## Syntax  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### Parameter  
 `plcid`  
 \[out\] " Adresse einer Variablen, die den Gebietsschemabezeichner für Benutzeroberflächenelemente empfängt, durch das Skriptmodul an.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_NOTIMPL`|Diese Methode ist nicht implementiert.  Verwenden Sie das systemdefinierte Gebietsschema.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
  
## Hinweise  
 Wenn diese Methode zurückgibt, `E_NOTIMPL` sollte der systemdefinierte Gebietsschemabezeichner verwendet werden.  
  
## Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)
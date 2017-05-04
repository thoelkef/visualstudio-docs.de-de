---
title: "IActiveScript::SetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptSite"
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::SetScriptSite
Informiert das Skriptmodul über die [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)\-Schnittstellensite, die vom Host bereitgestellt wird.  Rufen Sie diese Methode auf, bevor alle anderen [IActiveScript](../../winscript/reference/iactivescript.md)\-Schnittstellenmethoden verwendet wird.  
  
## Syntax  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### Parameter  
 `pScriptSite`  
 \[in\] Adresse in der vom Host angegebenen mit dieser Instanz des Skriptmoduls zugeordnet werden Skriptsite.  Die Website muss diese Skriptmodulinstanz eindeutig zugewiesen werden; kann nicht mit anderen Skriptmodulen freigegeben werden.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_FAIL`|Ein nicht spezifizierter Fehler aufgetreten; das Skriptmodul war nicht möglich, die Site zu initialisieren zu beenden.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, wurde bereits eine Website festgelegt\).|  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)
---
title: "IActiveScript::GetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptSite"
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::GetScriptSite
Ruft das Site\-Objekt ab, das dem Windows Script\-Modul zugeordnet ist.  
  
## Syntax  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### Parameter  
 `iid`  
 \[in\] Bezeichner der angeforderten Schnittstelle.  
  
 `ppvSiteObject`  
 \[out\] Adresse des Speicherorts, der den Schnittstellenzeiger zum Site\-Objekt des Hosts empfängt.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_NOINTERFACE`|Die angegebene Schnittstelle wird nicht unterstützt.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`S_FALSE`|Keine Site ist festgelegt wurde; der `ppvSiteObject`\-Parameter wird in `NULL` festgelegt.|  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)
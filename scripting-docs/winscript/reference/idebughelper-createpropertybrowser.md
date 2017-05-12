---
title: "IDebugHelper::CreatePropertyBrowser | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowser
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowser"
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowser
Gibt einen Eigenschaftenbrowser zurück, der eine VARIANTE umschließt.  
  
## Syntax  
  
```  
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### Parameter  
 `pvar`  
 \[in\] zu suchen Stammvariante.  
  
 `bstrName`  
 \[in\] Name, Seitenstamm zu geben.  
  
 `pdat`  
 \[in\] einer Tabelle in der, um Eigenschaften anfordern.  Wenn dieser Parameter NULL ist, wird kein Marshalling ausgeführt.  
  
 `ppdob`  
 \[out\] Der Eigenschaftenbrowser.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt einen Eigenschaftenbrowser zurück, der eine VARIANTE umschließt.  
  
## Siehe auch  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper\-Schnittstelle](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)
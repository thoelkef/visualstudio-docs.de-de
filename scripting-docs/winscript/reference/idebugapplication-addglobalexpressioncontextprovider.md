---
title: "IDebugApplication::AddGlobalExpressionContextProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.AddGlobalExpressionContextProvider
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::AddGlobalExpressionContextProvider"
ms.assetid: 35db7124-6970-4e45-8f00-ecdf21e9f5cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::AddGlobalExpressionContextProvider
Fügt einen globalen Ausdruckskontextanbieter dieser Anwendung hinzu.  
  
## Syntax  
  
```  
HRESULT AddGlobalExpressionContextProvider(  
   IProvideExpressionContexts*  pdsfs,  
   DWORD_PTR*                   pdwCookie  
);  
```  
  
#### Parameter  
 `pdsfs`  
 \[in\] Der globale dieser Anwendung hinzuzufügen, Kontextanbieter.  
  
 `pdwCookie`  
 \[out\] Ein Cookie, das verwendet wird, um diesen globalen Ausdruckskontextanbieter von der Anwendung zu entfernen.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode fügt einen globalen Ausdruckskontextanbieter dieser Anwendung hinzu.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)
---
title: "IDebugApplication::RemoveGlobalExpressionContextProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.RemoveGlobalExpressionContextProvider
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::RemoveGlobalExpressionContextProvider"
ms.assetid: ace638a3-ed34-4d20-8404-45c684aaaf1a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::RemoveGlobalExpressionContextProvider
Entfernt einen globalen Ausdruckskontextanbieter aus der Anwendung.  
  
## Syntax  
  
```  
HRESULT RemoveGlobalExpressionContextProvider(  
   DWORD_PTR  dwCookie  
);  
```  
  
#### Parameter  
 `dwCookie`  
 \[in\] Der das Cookie durch die `AddGlobalExpressionContextProvider`\-Methode zurück, der als globale Kontextanbieter hinzugefügt wurde.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Die `RemoveGlobalExpressionContextProvider`\-Methode entfernt einen globalen Ausdruckskontextanbieter aus der Anwendung.  
  
## Siehe auch  
 [IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)   
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)
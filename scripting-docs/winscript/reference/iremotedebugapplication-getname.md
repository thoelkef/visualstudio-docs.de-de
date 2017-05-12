---
title: "IRemoteDebugApplication::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.GetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::GetName"
ms.assetid: 3a8e8a4b-d7d4-40e5-97a1-f6d18db2e9c4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::GetName
Gibt den Namen dieses Anwendungsknotens zurück.  
  
## Syntax  
  
```  
HRESULT GetName(  
   BSTR*  pbstrName  
);  
```  
  
#### Parameter  
 `pbstrName`  
 \[out\] Name dieses Anwendungsknotens.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt den Namen dieses Anwendungsknotens zurück.  
  
## Siehe auch  
 [IRemoteDebugApplication\-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)
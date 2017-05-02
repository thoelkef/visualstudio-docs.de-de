---
title: "IProcessDebugManager::CreateApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.CreateApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::CreateApplication"
ms.assetid: d6b646f2-8af0-445c-ae7e-a9772042b3a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::CreateApplication
Erstellt ein neues Debug\- Anwendungsobjekt für diese Anwendung.  
  
## Syntax  
  
```  
HRESULT CreateApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### Parameter  
 `ppda`  
 \[out\] Die Debug\- Anwendungsobjekt für diese Anwendung.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Das Objekt, das ein erstellt wird, hat keinen Namen und wird nicht zur Liste der laufenden Anwendung hinzugefügt.  Verwenden Sie `IProcessDebugManager::AddApplication`, um die MFC\-Debugbuilds der Anwendung Anwendungsliste hinzuzufügen.  
  
## Siehe auch  
 [IProcessDebugManager\-Schnittstelle](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)
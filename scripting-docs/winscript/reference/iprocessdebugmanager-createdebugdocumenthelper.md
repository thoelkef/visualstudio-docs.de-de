---
title: "IProcessDebugManager::CreateDebugDocumentHelper | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.CreateDebugDocumentHelper
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::CreateDebugDocumentHelper"
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::CreateDebugDocumentHelper
Erstellt ein neues debuggen Dokumentenhilfe für diese Anwendung.  
  
## Syntax  
  
```  
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### Parameter  
 `punkOuter`  
 \[in\] Wenn das zurückgegebene Objekt aggregiert werden soll, ist `punkOuter` ein Schnittstellenzeiger zu steuernden `IUnknown`.  Andernfalls ist es ein NULL\-Zeiger.  
  
 `pddh`  
 \[out\] Die Debug\- Dokumentenhilfeobjekt für diese Anwendung.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode erstellt ein neues debuggen Dokumentenhilfe für diese Anwendung.  
  
## Siehe auch  
 [IProcessDebugManager\-Schnittstelle](../../winscript/reference/iprocessdebugmanager-interface.md)
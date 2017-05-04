---
title: "IProcessDebugManager::GetDefaultApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.GetDefaultApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::GetDefaultApplication"
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::GetDefaultApplication
Gibt ein Standard Anwendungsobjekt für den aktuellen Prozess zurück.  
  
## Syntax  
  
```  
HRESULT GetDefaultApplication(  
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
 Diese Methode erstellt ein neues Anwendungsobjekt Debug\- und fügt es der Liste der laufenden Anwendung, ggf. hinzu.  
  
 Sprachmodule sollten die Anwendung verwenden, die von der `GetDefaultApplication`\-Methode angegeben wird, wenn sie auf einen Host ausgeführt werden, der keine Anwendung bereitstellt.  
  
## Siehe auch  
 [IProcessDebugManager\-Schnittstelle](../../winscript/reference/iprocessdebugmanager-interface.md)
---
title: 'Imachinedebugmanager:: addapplikation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ff617ac96c0eb3498b796d4f7fe49f95e1cc96
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573968"
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
Fügt der Liste der laufenden Anwendungen eine Anwendung hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pda`  
 in Anwendung in der Liste der laufenden Anwendungen.  
  
 `pdwAppCookie`  
 vorgenommen Ein Cookie, das verwendet wird, um die Anwendung aus dem Machine Debug-Manager zu entfernen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird vom Process Debug Manager aufgerufen, wenn `IProcessDebugManager::AddApplication` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Imachinedebugmanager-Schnittstelle](../../winscript/reference/imachinedebugmanager-interface.md)    
 [Imachinedebugmanager:: RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md) -   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)
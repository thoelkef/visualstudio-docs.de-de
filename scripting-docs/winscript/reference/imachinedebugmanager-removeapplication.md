---
title: 'Imachinedebugmanager:: RemoveApplication | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.RemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::RemoveApplication
ms.assetid: 873509ce-e638-484a-b2a2-489a8ce7dbfe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87951e55a7cfcfef1a366f79c380948c7651ed12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573940"
---
# <a name="imachinedebugmanagerremoveapplication"></a>IMachineDebugManager::RemoveApplication
Entfernt eine Anwendung aus der Liste der laufenden Anwendungen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwAppCookie`  
 in Das Cookie, das bereitgestellt wird, als die Anwendung der Anwendungsliste hinzugefügt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird vom Process Debug Manager aufgerufen, wenn `IProcessDebugManager::RemoveApplication` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Imachinedebugmanager:: addapplikation](../../winscript/reference/imachinedebugmanager-addapplication.md) -   
 [Imachinedebugmanager-Schnittstelle](../../winscript/reference/imachinedebugmanager-interface.md)    
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)
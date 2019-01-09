---
title: IProcessDebugManager::RemoveApplication | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.RemoveApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::RemoveApplication
ms.assetid: 334e869d-81ae-4d30-9e89-89763ad4f184
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c163f756e426cab9ce36c1c8343b142bf76aafd6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086514"
---
# <a name="iprocessdebugmanagerremoveapplication"></a>IProcessDebugManager::RemoveApplication
Entfernt eine Anwendung aus der ausgeführten Anwendungsliste.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwAppCookie`  
 [in] Das Cookie gebotenen `IProcessDebugManager::AddApplication` Wenn die Anwendung der Liste hinzugefügt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode entfernt eine Anwendung aus der ausgeführten Anwendungsliste.  
  
## <a name="see-also"></a>Siehe auch  
 [Iprocessdebugmanager:: Addapplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)   
 [IProcessDebugManager-Schnittstelle](../../winscript/reference/iprocessdebugmanager-interface.md)
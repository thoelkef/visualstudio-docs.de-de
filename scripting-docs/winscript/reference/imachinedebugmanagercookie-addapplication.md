---
title: 'Imachinedebugmanagercookie:: addapplikation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::AddApplication
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da436308c71a66d3070d42128d8da03ae88d2935
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573911"
---
# <a name="imachinedebugmanagercookieaddapplication"></a>IMachineDebugManagerCookie::AddApplication
Fügt der Liste der laufenden Anwendungen eine Anwendung hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pda`  
 in Anwendung in der Liste der laufenden Anwendungen.  
  
 `dwDebugAppCookie`  
 in Ein Cookie, das die debugginganwendung identifiziert.  
  
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
 [Imachinedebugmanagercookie-Schnittstelle](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)
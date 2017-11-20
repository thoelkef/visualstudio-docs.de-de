---
title: IMachineDebugManagerCookie::AddApplication | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManagerCookie.AddApplication
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManagerCookie::AddApplication
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c452c4fe2826c7c5372c7598a14731e14077925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookieaddapplication"></a>IMachineDebugManagerCookie::AddApplication
Fügt eine Anwendung mit der Ausführung Anwendungsliste.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pda`  
 [in] Anwendung mit der Ausführung Anwendungsliste.  
  
 `dwDebugAppCookie`  
 [in] Ein Cookie, das die Debuganwendung bezeichnet.  
  
 `pdwAppCookie`  
 [out] Ein Cookie, mit dem die Anwendung von Machine Debug-Manager zu entfernen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, von der Debug-Prozess-Manager immer `IProcessDebugManager::AddApplication` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IMachineDebugManagerCookie-Schnittstelle](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)
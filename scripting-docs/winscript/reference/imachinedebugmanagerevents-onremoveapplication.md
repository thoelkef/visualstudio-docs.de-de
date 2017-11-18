---
title: IMachineDebugManagerEvents::onRemoveApplication | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManagerEvents.onRemoveApplication
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManagerEvents::onRemoveApplication
ms.assetid: 3ba71bd8-fd69-4a41-99c6-c736c416f227
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe727b65c8a74962cf6a88ce4ab36ad975b26231
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagereventsonremoveapplication"></a>IMachineDebugManagerEvents::onRemoveApplication
Behandelt das Ereignis, wenn die Ausführung eine Anwendung entfernt wird Anwendungsliste.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT onRemoveApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pda`  
 [in] Anwendung, die die Ausführung von entfernte Anwendungsliste.  
  
 `dwAppCookie`  
 [in] Das Cookie bereitgestellt, wenn die Anwendung aus der Anwendungsliste hinzugefügt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt an, dass die Ausführung eine Anwendung entfernt wurde Anwendungsliste.  
  
## <a name="see-also"></a>Siehe auch  
 [IMachineDebugManagerEvents-Schnittstelle](../../winscript/reference/imachinedebugmanagerevents-interface.md)   
 [IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)
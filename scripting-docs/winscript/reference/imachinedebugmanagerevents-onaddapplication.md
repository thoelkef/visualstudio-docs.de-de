---
title: 'Imachinedebugmanagerevents:: onaddapplikation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerEvents.onAddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerEvents::onAddApplication
ms.assetid: 00a54b91-36d5-430d-b654-5e2abe5300cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe710ce9a126e344fc88024b7bf5fd2b993e31b3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576107"
---
# <a name="imachinedebugmanagereventsonaddapplication"></a>IMachineDebugManagerEvents::onAddApplication
Behandelt das-Ereignis, wenn eine Anwendung zur Liste der laufenden Anwendungen hinzugefügt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onAddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pda`  
 in Die Anwendung, die der Liste der laufenden Anwendungen hinzugefügt wurde.  
  
 `dwAppCookie`  
 in Das Cookie, das bereitgestellt wird, als die Anwendung der Anwendungsliste hinzugefügt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt an, dass der Liste der laufenden Anwendungen eine Anwendung hinzugefügt wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Imachinedebugmanagerevents-Schnittstelle](../../winscript/reference/imachinedebugmanagerevents-interface.md)    
 [IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)
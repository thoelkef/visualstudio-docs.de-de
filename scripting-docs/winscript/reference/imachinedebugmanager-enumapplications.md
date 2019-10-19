---
title: 'Imachinedebugmanager:: umumapplications | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.EnumApplications
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::EnumApplications
ms.assetid: 5d833db4-fd9b-4e61-bebb-130faede5a77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518e7fd2f22a89e767dec7cc2c7b03ab811b2904
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573953"
---
# <a name="imachinedebugmanagerenumapplications"></a>IMachineDebugManager::EnumApplications
Gibt einen Enumerator der aktuellen Liste ausgelaufteter Anwendungen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppeda`  
 vorgenommen Enumerator, der die aktuelle Liste der ausgelaufenden Anwendungen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt einen Enumerator der aktuellen Liste ausgelaufteter Anwendungen zurück. Die Debugger-IDE verwendet diese Methode, um Anwendungen zu Debuggingzwecken anzuzeigen und anzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [IMachineDebugManager-Schnittstelle](../../winscript/reference/imachinedebugmanager-interface.md)
---
title: 'Iremotedebuapplication:: queryalive | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.QueryAlive
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::QueryAlive
ms.assetid: 08e49d3b-6fb3-4438-960e-f05395ba9b17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3edc4fc007a2372c429b0bbece394cb1c30a2770
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577473"
---
# <a name="iremotedebugapplicationqueryalive"></a>IRemoteDebugApplication::QueryAlive
Gibt an, ob die Anwendung reaktionsfähig ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt an, ob die Anwendung reaktionsfähig ist. Implementierungen dieser Methode sollten immer `S_OK` zurückgeben.  
  
 Wenn der Anwendungsprozess unerwartet beendet wird, gibt com einen Fehler vom Marshalling-Proxy für Aufrufe dieser Methode zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)
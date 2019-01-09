---
title: IRemoteDebugApplication::ConnectDebugger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ConnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ConnectDebugger
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e6db85ab30d04ebaf24ec0e955aab529ff8799d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088854"
---
# <a name="iremotedebugapplicationconnectdebugger"></a>IRemoteDebugApplication::ConnectDebugger
Verbindet einen Debugger an diese Anwendung an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pad`  
 [in] Der Debugger auf diese Anwendung angefügt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Ein Debugger ist bereits auf diese Anwendung verbunden.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Anwendung kann nur einen Debugger, die Verbindung zu einem Zeitpunkt verfügen. Diese Methode schlägt fehl, wenn bereits ein Debugger verbunden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)   
 [IRemoteDebugApplication-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)
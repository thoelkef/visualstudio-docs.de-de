---
title: IDebugSessionProviderEx:StartDebugSession | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSessionProviderEx:StartDebugSession
apilocation:
- scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94d26e99b951779b29bb0456f823d19bfa6193bc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093430"
---
# <a name="idebugsessionproviderexstartdebugsession"></a>IDebugSessionProviderEx:StartDebugSession
Startet eine Debugsitzung mit der angegebenen Anwendung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pda`  
 [in] Gibt die Anwendung debuggen.  
  
 `fQuery`  
 [in] "True" gibt eine Abfrage an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode initiiert eine Debugsitzung mit der angegebenen Anwendung. Der Debugger sollte Aufrufen `IRemoteDebugApplication::ConnectDebugger` vor der Rückgabe von diesem Aufruf.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSessionProviderEx-Schnittstelle](../../winscript/reference/idebugsessionproviderex-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)
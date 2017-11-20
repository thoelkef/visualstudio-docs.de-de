---
title: IDebugSessionProviderEx:StartDebugSession | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSessionProviderEx:StartDebugSession
apilocation: scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6f68d5bef91a71d475ea8b0c5131b5945b4c930
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionproviderexstartdebugsession"></a>IDebugSessionProviderEx:StartDebugSession
Startet eine Debugsitzung mit der angegebenen Anwendung an.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 Diese Methode startet eine Debugsitzung mit der angegebenen Anwendung. Der Debugger sollte Aufrufen `IRemoteDebugApplication::ConnectDebugger` vor der Rückgabe von diesen Aufruf.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSessionProviderEx-Schnittstelle](../../winscript/reference/idebugsessionproviderex-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)
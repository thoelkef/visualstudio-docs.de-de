---
title: IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationThread.SetNextStatement
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb23fa643f9a2333e17239a74d0da2f75e1ea791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Erzwingt die Ausführung so nah wie möglich an den Kontext angegebenen Code im Kontext des angegebenen Rahmens ermöglicht.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStackFrame`  
 [in] Die Stack-Frame-Objekts. Dieses Argument kann NULL sein; das bedeutet, dass der aktuelle Stapelrahmen verwendet werden soll.  
  
 `pCodeContext`  
 [in] Der Codekontext. Dieses Argument kann NULL sein; das bedeutet, dass der aktuelle Codekontext verwendet werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erzwingt die Ausführung so nah wie möglich an den Codekontext gemäß fortgesetzt `pCodeContext`, im Kontext des Frames gemäß `pStackFrame`. Von diesen Argumenten ist möglicherweise `NULL`, den aktuellen Frame oder Kontext darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplicationThread-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)
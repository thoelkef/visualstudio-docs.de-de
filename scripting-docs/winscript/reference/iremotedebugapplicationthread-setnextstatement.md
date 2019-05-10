---
title: IRemoteDebugApplicationThread::SetNextStatement | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c4b19322a15e92adcf2609c479af6b21e2078bd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788139"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Erzwingt, dass die Ausführung so nah wie möglich an den angegebenen Code-Kontext, in dem Kontext des angegebenen Rahmens fortgesetzt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStackFrame`  
 [in] Das Stack-Frame-Objekt. Dieses Argument kann NULL sein, Dies impliziert, dass der aktuelle Stapelrahmen verwendet werden soll.  
  
 `pCodeContext`  
 [in] Der Codekontext. Dieses Argument kann NULL sein, Dies impliziert, dass der aktuelle Codekontext verwendet werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erzwingt die Ausführung weiterhin so nah wie möglich auf den Codekontext anhand des `pCodeContext`, im Kontext des Frames gemäß `pStackFrame`. Eines dieser Argumente möglicherweise `NULL`, die die aktuellen Frame oder das Kontextmenü darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplicationThread-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)
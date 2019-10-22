---
title: 'Iremotedebugapplicationthread:: SetNextStatement | Microsoft-Dokumentation'
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
ms.openlocfilehash: 71e690d0e5b7567aabc88aabde907b67517f12aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575509"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Erzwingt, dass die Ausführung so nah wie möglich an den angegebenen Code Kontext im Kontext des angegebenen Frames fortgesetzt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStackFrame`  
 in Das Stapel Rahmen Objekt. Dieses Argument kann NULL sein, was impliziert, dass der aktuelle Stapel Rahmen verwendet werden soll.  
  
 `pCodeContext`  
 in Der Code Kontext. Dieses Argument kann NULL sein, was impliziert, dass der aktuelle Code Kontext verwendet werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erzwingt das Fortsetzen der Ausführung so nah wie möglich an den durch `pCodeContext` angegebenen Code Kontext im Kontext des Frame, der durch `pStackFrame` angegeben wird. Beide Argumente können `NULL` werden, die den aktuellen Frame oder Kontext darstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [IRemoteDebugApplicationThread-Schnittstelle](../../winscript/reference/iremotedebugapplicationthread-interface.md)
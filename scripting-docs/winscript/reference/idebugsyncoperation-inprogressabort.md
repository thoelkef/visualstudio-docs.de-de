---
title: 'Idebugsyncoperation:: inprogressabort | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40974c738c071e52648297ac90a0ab89d9681435
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576671"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Bricht einen Vorgang ab, der in einem anderen Thread ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Vorgang kann nicht abgebrochen werden.|  
|`E_ABORT`|Der Vorgang konnte nicht abgeschlossen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Der Process Debug Manager ruft diese Methode innerhalb des Debugger-Threads auf, um einen Vorgang abzubrechen, der in einem anderen Thread ausgeführt wird.  
  
 Wenn die `InProgressAbort` Methode den Vorgang nicht beenden kann, wird `E_ABORT` so bald wie möglich zurückgegeben. Diese Methode kann `E_NOTIMPL` zurückgeben, wenn der Vorgang nicht abgebrochen werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSyncOperation-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md)
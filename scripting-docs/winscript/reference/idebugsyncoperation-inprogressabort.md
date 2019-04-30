---
title: IDebugSyncOperation::InProgressAbort | Microsoft-Dokumentation
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
ms.openlocfilehash: a794ea70d6d2fe937afb311e6961d53f22bd7ac2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004835"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Bricht eine laufende Operation auf einem anderen Thread ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Vorgang kann nicht abgebrochen werden.|  
|`E_ABORT`|Der Vorgang konnte nicht abgeschlossen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Den prozessbasierten Debugmanager ruft diese Methode aus, eine Operation abzubrechen, die in einem anderen Thread wird vom Debugger-Thread.  
  
 Wenn die `InProgressAbort` Methode: der Vorgang kann nicht abgeschlossen werden, gibt `E_ABORT` so bald wie möglich. Diese Methode kann zurückgeben `E_NOTIMPL` , wenn der Vorgang kann nicht abgebrochen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSyncOperation-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md)
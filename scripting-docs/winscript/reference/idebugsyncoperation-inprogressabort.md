---
title: IDebugSyncOperation::InProgressAbort | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df0b0ca1d775d4d99e1da5f88a207bd4f78f99b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Bricht eine laufende Operation auf einen anderen Thread ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Vorgang kann nicht abgebrochen werden.|  
|`E_ABORT`|Der Vorgang konnte nicht abgeschlossen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Der Debug-Prozess-Manager ruft diese Methode innerhalb der debugthread, eine Operation abzubrechen, die in einem anderen Thread ausgeführt wird.  
  
 Wenn die `InProgressAbort` Methode der Vorgang kann nicht abgeschlossen werden, gibt es `E_ABORT` so bald wie möglich. Diese Methode kann zurückgeben `E_NOTIMPL` , wenn der Vorgang kann nicht abgebrochen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSyncOperation-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md)
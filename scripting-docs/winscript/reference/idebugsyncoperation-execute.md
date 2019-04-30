---
title: IDebugSyncOperation::Execute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2bc204169ff94a240e363eb8caa35ec8c7de9be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004880"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Synchron den Vorgang ausführt, und gibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppunkResult`  
 [out] Der Objektparameter, die vom Vorgang zurückgegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_ABORT`|Der Vorgang wurde abgebrochen, durch den Aufruf der `IDebugSyncOperation::InProgressAbort` Methode.|  
  
## <a name="remarks"></a>Hinweise  
 Den prozessbasierten Debugmanager in der Ziel-Thread Ruft die `Execute` Methode synchron.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSyncOperation-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md)
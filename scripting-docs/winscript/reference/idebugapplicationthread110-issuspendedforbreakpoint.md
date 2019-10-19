---
title: 'IDebugApplicationThread110:: issuspendforbreakpoint | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsSuspendedForBreakPoint
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0e70993b95ccffcf6041bb04f37af90667fc4fd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574458"
---
# <a name="idebugapplicationthread110issuspendedforbreakpoint"></a>IDebugApplicationThread110::IsSuspendedForBreakPoint
Bestimmt, ob [IDebugApplicationThreadEvents110:: onsuspendforbreakpoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) für diesen Thread aufgerufen wurde und noch nicht abgeschlossen wurde.  
  
> [!IMPORTANT]
> Die [IDebugApplicationThread110-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfIsSuspended`  
 [out] `true`, wenn der Thread für einen Haltepunkt angehalten wird, andernfalls `false`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationThread110-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md)
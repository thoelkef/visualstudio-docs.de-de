---
title: 'IDebugApplicationThreadEvents110:: onsuspendforbreakpoint | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
ms.assetid: 224245ac-2aa2-43ae-97ed-493afc3d0122
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5d73d7769dd48889a75da63da64be1d2977a088
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573334"
---
# <a name="idebugapplicationthreadevents110onsuspendforbreakpoint"></a>IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
Bestimmt, ob der Thread für einen Haltepunkt vollständig angehalten wurde und die normale Ausführung noch nicht fortgesetzt wurde.  
  
> [!IMPORTANT]
> Die [IDebugApplicationThreadEvents110-Schnittstelle](../../winscript/reference/idebugapplicationthreadevents110-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT OnSuspendForBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode hat keine Parameter.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationThreadEvents110-Schnittstelle](../../winscript/reference/idebugapplicationthreadevents110-interface.md)
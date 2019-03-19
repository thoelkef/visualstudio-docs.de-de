---
title: IDebugApplicationThreadEvents110::OnSuspendForBreakPoint | Microsoft-Dokumentation
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
ms.openlocfilehash: 1e6a663d6c1e504d8e10ea26d7d5b395b5ba8025
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153083"
---
# <a name="idebugapplicationthreadevents110onsuspendforbreakpoint"></a>IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
Bestimmt, ob der Thread vollständig für einen Haltepunkt angehalten wurde und noch nicht normalen Ausführung fortgesetzt wurde.  
  
> [!IMPORTANT]
>  [IDebugApplicationThreadEvents110-Schnittstelle](../../winscript/reference/idebugapplicationthreadevents110-interface.md) wird implementiert von PDM V11. 0 und höher. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT OnSuspendForBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode hat keine Parameter.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationThreadEvents110-Schnittstelle](../../winscript/reference/idebugapplicationthreadevents110-interface.md)
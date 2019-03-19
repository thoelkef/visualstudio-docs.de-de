---
title: IDebugApplication::StepOutComplete | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04f8ecfb835199afa0a60f3fde3c8fbdc8812240
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153135"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Benachrichtigt prozessbasierten Debug-Manager, dass es sich bei eine Sprach-Engine im einschrittigen Modus zum an den Aufrufer zurückgegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sprach-Engines aufrufen im einschrittigen Modus diese Methode, unmittelbar bevor sie sich an ihren Aufrufer zurückgeben. Prozessbasierten Debug-Manager verwendet diese Gelegenheit, um die Skript-Engines zu informieren, die sie bei der ersten Gelegenheit umgebrochen werden soll. Diese Technik ist wie sprachübergreifende Schritt Modi implementiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)
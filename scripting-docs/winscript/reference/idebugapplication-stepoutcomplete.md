---
title: 'Idebugapplication:: stepoutcomplete | Microsoft-Dokumentation'
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
ms.openlocfilehash: f50d7e8a8936e52f4177450e7d163c4cfeaa55df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571035"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Benachrichtigt den Prozess-Debug-Manager, dass eine Sprach-Engine im Einzelschritt Modus im Begriff ist, zu Ihrem Aufrufer zurückzukehren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sprachmodule bezeichnen diese Methode im Einzelschritt Modus, kurz bevor Sie an ihren Aufrufer zurückgegeben werden. Der Process Debug Manager verwendet diese Gelegenheit, um alle anderen Skript-Engines zu benachrichtigen, dass Sie bei der ersten Gelegenheit unterbrechen sollten. Diese Technik ist die Implementierung von sprachübergreifenden Schritt Modi.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)
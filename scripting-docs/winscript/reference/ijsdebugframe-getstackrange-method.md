---
title: 'Ijsdebugframe:: GetStackRange-Methode | Microsoft Docs'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange-Methode
Gibt den Bereich der absoluten Adresse des logischen JavaScript-Stapelrahmens zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStart`  
 [out] Unterster Stapelzeiger des Frames.  
  
 `pEnd`  
 [out] Oberster Stapelzeiger des Frames.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist für die Zusammenführung überlappender Stapelüberwachungen nützlich, die aus mehreren Laufzeiten erfasst wird. Start und Ende Stapelzeiger können mehrere Stapelrahmen für physische Computer (für interpretierte Rahmen für die JavaScript-Laufzeit) umfassen. Start > beenden, wie der Stapel von hoch zu niedrig Adresse vergrößert.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugFrame-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)
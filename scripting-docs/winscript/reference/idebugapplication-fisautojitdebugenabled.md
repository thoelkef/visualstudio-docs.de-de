---
title: IDebugApplication::FIsAutoJitDebugEnabled | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FIsAutoJitDebugEnabled
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f594c5ce48ebd31a265ed438db176c5707d9b079
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990860"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Ermittelt, ob ein JIT-Debugger (Just-in-Time) für das automatische Debuggen von Dumb-Hosts registriert ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Methode erfolgreich ist und ein JIT-Debugger für das automatische Debuggen von Dumb-Hosts registriert ist, gibt die Methode `TRUE` zurück. Andernfalls wird `FALSE`zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermittelt, ob ein JIT-Debugger für das automatische Debuggen von Dumb-Hosts registriert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)
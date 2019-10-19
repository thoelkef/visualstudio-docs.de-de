---
title: 'Idebugapplication:: fsaudejitdebugenabled | Microsoft-Dokumentation'
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
ms.openlocfilehash: 9bf97a4d3985dd3dd32e582c689fde0ecd6f52e1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574987"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Bestimmt, ob ein JIT-Debugger (Just-in-Time) für das automatische Debuggen von stumm Hosts registriert ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Methode erfolgreich ist und ein JIT-Debugger für die automatische debugausführung von stumm Hosts registriert ist, gibt die Methode `TRUE` zurück. Andernfalls wird `FALSE` zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bestimmt, ob ein JIT-Debugger für die automatische Debugkonfiguration von stumm Hosts registriert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)
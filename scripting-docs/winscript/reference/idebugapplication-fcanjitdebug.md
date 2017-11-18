---
title: IDebugApplication::FCanJitDebug | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.FCanJitDebug
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ca6b990011252bde581168a272da1041dc24f41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
Bestimmt, ob ein Just-in-Time (JIT)-Debugger registriert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Methode erfolgreich ist, und ein JIT-Debugger registriert ist, gibt die Methode `TRUE`. Andernfalls wird zurückgegeben `FALSE`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bestimmt, ob ein JIT-Debugger registriert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)
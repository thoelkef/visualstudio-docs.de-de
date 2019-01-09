---
title: IDebugApplication::FCanJitDebug | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6808c8bb7e27e7b416e79b2f23e323c3ae3a528f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095354"
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
Bestimmt, ob ein just-in-Time (JIT)-Debugger registriert ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Methode erfolgreich ist, und ein JIT-Debugger registriert ist, gibt die Methode `TRUE`. Andernfalls wird `FALSE` zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird bestimmt, ob ein JIT-Debugger registriert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)
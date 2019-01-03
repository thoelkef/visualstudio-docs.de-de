---
title: IDebugProcess3::DisableENC | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c8d440783dbd6112e6f9918cd22388b4b8efbff0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921189"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Diese Methode explizit bearbeiten und Fortfahren deaktiviert zu diesem Vorgang (und alle Programme, die sie enthält). Ein benutzerdefinierten Port Lieferanten sollte immer zurückgeben `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `reason`  
 [in] Ein Wert aus der [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) Enumeration.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.  
  
> [!NOTE]
>  Ein benutzerdefinierten Port Lieferanten sollte immer zurückgeben `E_NOTIMPL`.  
  
## <a name="remarks"></a>Hinweise  
 Bearbeiten und Fortfahren für einen Prozess deaktiviert ist, kann diese erneut aktiviert werden nur durch Neustart des Prozesses.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
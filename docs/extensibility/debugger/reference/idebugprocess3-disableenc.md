---
title: IDebugProcess3::DisableENC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::DisableENC
helpviewer_keywords: IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fba3718052b708b5c5d88306c022ed9c397a99cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Diese Methode explizit bearbeiten und Fortfahren deaktiviert auf diesem Prozess (und alle Programme, die es enthält). Ein benutzerdefinierten Port Lieferanten sollten stets `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
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
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Ein benutzerdefinierten Port Lieferanten sollten stets `E_NOTIMPL`.  
  
## <a name="remarks"></a>Hinweise  
 Bearbeiten und Fortfahren für einen Prozess deaktiviert ist, kann erneut nur durch den Neustart des Prozesses aktiviert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
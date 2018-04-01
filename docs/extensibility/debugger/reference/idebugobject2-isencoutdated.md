---
title: IDebugObject2::IsEncOutdated | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 757e533f855ab1bc276e484d46d6866b0dd6ca40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Diese Methode bestimmt, ob die bearbeiten und Fortfahren Status dieses Objekts "oder" des übergeordneten Containers veraltet ist. Diese Methode und gibt immer eine benutzerdefinierte ausdrucksauswertung nicht implementiert `E_NOTIMPL`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfEncOutdated`  
 [out] Ungleich Null (`TRUE`) ist der Status bearbeiten und Fortfahren nicht mehr aktuell, 0 (null) (`FALSE`) wird jedoch nicht.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Eine benutzerdefinierte ausdrucksauswertung sollte stets `E_NOTIMPL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
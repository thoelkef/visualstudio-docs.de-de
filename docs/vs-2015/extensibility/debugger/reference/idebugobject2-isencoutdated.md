---
title: IDebugObject2::IsEncOutdated | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cce9b8451eaf5e8304c7ec974fccb929b12066f0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912317"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode bestimmt, ob der Bearbeiten und Fortfahren-Status dieses Objekts oder des übergeordneten Containers veraltet ist. Diese Methode und gibt immer eine benutzerdefinierte ausdrucksauswertung nicht implementiert `E_NOTIMPL`.  
  
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
 [out] Ungleich Null (`TRUE`), wenn der Bearbeiten und Fortfahren-Status nicht mehr aktuell ist, NULL (`FALSE`) ist dies nicht.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Eine benutzerdefinierte ausdrucksauswertung sollte immer zurückgeben `E_NOTIMPL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)


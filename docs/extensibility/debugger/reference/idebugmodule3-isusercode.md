---
title: IDebugModule3::IsUserCode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f852869069125e0a215cffd9c4c4f6eb15a2ab39
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007450"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Ruft Informationen zu gibt an, ob das Modul Benutzercode oder nicht darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfUser`  
 [out] Ungleich Null (`TRUE`), wenn das Modul Benutzercode darstellt, NULL (`FALSE`), wenn dies nicht der Fall.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
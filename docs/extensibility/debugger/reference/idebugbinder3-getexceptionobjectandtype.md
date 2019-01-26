---
title: IDebugBinder3::GetExceptionObjectAndType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04fbb6c711daccc6c40f5560d981906cd46cd37d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007398"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Diese Methode ruft die Ausnahme, die einem Objekt zugeordneten ab, sofern vorhanden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppException`  
 [out] Gibt das Objekt, das die Ausnahme darstellt.  
  
 `ppField`  
 [out] Gibt das Objekt, das ein bestimmtes Feld, das die Ausnahme verursacht haben kann (Dies kann ein null-Wert sein) darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Um zu überprüfen, ob eine Ausnahme auftritt, überprüfen Sie den Rückgabewert von `ppException`: Wenn sie einen null-Wert, wird keine Ausnahme, die diesem Objekt zugeordnet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
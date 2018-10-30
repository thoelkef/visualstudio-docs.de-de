---
title: IDebugBinder3::GetExceptionObjectAndType | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61f82cdeda76cd8660fff47e30edf37c81d154f5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867792"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Diese Methode ruft die Ausnahme, die einem Objekt zugeordneten ab, sofern vorhanden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
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
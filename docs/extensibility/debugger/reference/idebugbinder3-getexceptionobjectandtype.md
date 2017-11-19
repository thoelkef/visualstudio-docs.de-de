---
title: IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords: IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b533423da8152dd23df6d32da3361c99ad032b7e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
> [!NOTE]
>  Um zu überprüfen, ob eine Ausnahme auftritt, überprüfen Sie den Rückgabewert von `ppException`: Wenn es ist ein null-Wert, es werden keine Ausnahmen dieses Objekt zugeordnet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
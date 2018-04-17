---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c81bdc6586766cb4a241bf29e653cb1b10f66f2f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Ruft den Namen des Ports ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrPortName`  
 [out] Gibt den Namen des Ports.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) Schnittstelle ist in der Regel übergeben aus einem debugpaket (Client) an einen Lieferanten Port (Server), um eine Verbindung zu erhalten, einen Port. Das debugpaket und den Lieferanten Port kennen die möglichen Optionen für den Port. Wenn Sie eine einfache Zeichenfolge den Port kann beschrieben werden, und klicken Sie dann die `IDebugPortRequest2::GetPortName` Methode verfügt über genügend Informationen zum Herstellen die Verbindung. Andernfalls können weitere Schnittstellen bereitgestellt werden, durch den Client, der vom Server mit abgerufen werden kann `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
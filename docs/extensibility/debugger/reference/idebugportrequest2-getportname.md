---
title: IDebugPortRequest2::GetPortName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd5033926987ef1a2673380a4f7d76dc1b0cb0c0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962731"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Ruft den Namen des Ports.  
  
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
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) Schnittstelle wird in der Regel aus einem debugpaket (Client) an übergeben eines portanbieters (Server), um eine Verbindung zu erhalten. mit einem Port. Sowohl das debugpaket und Anschlusslieferanten sind die möglichen Optionen für den Port kennen. Wenn Sie eine einfache Zeichenfolge beschrieben, kann den Port, und klicken Sie dann die `IDebugPortRequest2::GetPortName` Methode weist genügend Informationen zum Herstellen die Verbindung. Andernfalls können weitere Schnittstellen bereitgestellt werden, durch den Client, der vom Server mit abgerufen werden kann `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
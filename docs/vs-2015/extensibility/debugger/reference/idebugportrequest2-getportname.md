---
title: IDebugPortRequest2::GetPortName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff9ff4fb0a682b378bd35406f8e196d6b6c8a61e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510670"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugPortRequest2::GetPortName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportrequest2-getportname).  
  
Ruft den Namen des Ports.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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


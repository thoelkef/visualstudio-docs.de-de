---
title: 'IDebugPortSupplier2:: AddPort | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf5bf281e794bde04ae0c2e86c6d27edb7edc5a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188295"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Fügt einen Port hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRequest`  
 in Ein [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) -Objekt, das den hinzu zufügenden Port beschreibt.  
  
 `ppPort`  
 vorgenommen Gibt ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) -Objekt zurück, das den Port darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode erstellt tatsächlich den angeforderten Port und fügt ihn der internen Liste aktiver Ports des Port Anbieters hinzu. Die [canaddport](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) -Methode kann zuerst aufgerufen werden, um mögliche zeitaufwändige Verzögerungen zu vermeiden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)

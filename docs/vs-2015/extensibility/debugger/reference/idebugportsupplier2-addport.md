---
title: IDebugPortSupplier2::AddPort | Microsoft-Dokumentation
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
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a8516402e3caa7bcd7abbdc5a1ccd93ce40275e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514234"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugPortSupplier2::AddPort](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplier2-addport).  
  
Fügt einen Port an.  
  
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
 [in] Ein [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) -Objekt, das beschreibt, den Port hinzugefügt werden.  
  
 `ppPort`  
 [out] Gibt eine [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Objekt, das den Port darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird den angeforderten Port sowie das Hinzufügen zu den Anschlusslieferanten internen Liste der aktiven Ports erstellt. Die [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) Methode kann zuerst aufgerufen werden, um mögliche zeitaufwändige Verzögerungen zu vermeiden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)


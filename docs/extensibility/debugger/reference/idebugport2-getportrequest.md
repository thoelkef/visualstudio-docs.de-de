---
title: IDebugPort2::GetPortRequest | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 58968a42b433ab87f556ff2dfbeb899fdcf3a681
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Ruft die Beschreibung eines Ports, die zuvor verwendet wurde, um den Port (falls verfügbar) zu erstellen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppRequest`  
 [out] Gibt eine [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) Objekt, das die Anforderung, die verwendet wurde, erstellen Sie den Port darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  Gibt `E_PORT_NO_REQUEST` Wenn mit ein Port nicht erstellt wurde ein [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) Port-Anforderung.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

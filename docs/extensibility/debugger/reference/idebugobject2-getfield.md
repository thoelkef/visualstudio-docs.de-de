---
title: IDebugObject2::GetField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject2::GetField
helpviewer_keywords:
- IDebugObject2::GetField method
ms.assetid: add6a6b5-e752-47dd-9613-29206ea809b0
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 20b25e5354df648ba0265d156dbbf1e27add3e05
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2getfield"></a>IDebugObject2::GetField
Ruft den Typ dieses Objekts ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetField(  
 IDebugField** ppField  
);  
```  
  
```csharp  
int GetField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppField`  
 [out] Gibt eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt ggf. einen null-Wert.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Feld beschreibt den Typ des Objekts.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
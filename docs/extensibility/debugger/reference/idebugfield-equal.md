---
title: IDebugField::Equal | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7fdfc2abd407c586c949ade4e8085e282fb465a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984352"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Diese Methode vergleicht dieses Feld mit dem angegebenen Feld hinsichtlich ihrer Gleichheit.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pField`  
 [in] Das Feld, in dieses Objekt verglichen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt zurück, wenn die Felder identisch sind, `S_OK`. Gibt zurück, wenn die Felder unterscheiden, `S_FALSE.` wird, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
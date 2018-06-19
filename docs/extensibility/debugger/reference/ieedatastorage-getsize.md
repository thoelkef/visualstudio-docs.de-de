---
title: IEEDataStorage::GetSize | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9fb6c315971c5d7886626239387d6c6ff501ed0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119827"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Gibt die Anzahl der Bytes, die in diesem Objekt enthaltene zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSize(  
   ULONG* size  
);  
```  
  
```csharp  
int GetSize(  
   out uint size  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `size`  
 [out] Die Anzahl der Bytes, die in diesem Objekt enthalten.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) Methode, um die tatsächlichen Datenbytes abzurufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
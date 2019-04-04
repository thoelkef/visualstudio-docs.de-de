---
title: IEEDataStorage::GetSize | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c76ae583d089b23d21664c9e312d2486a14c2aa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959223"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Anzahl der Bytes, die in diesem Objekt enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [out] Die Anzahl der Bytes, die in diesem Objekt enthalten sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) Methode, um die tatsächlichen Datenbytes abzurufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)

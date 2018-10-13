---
title: IEEDataStorage::GetSize | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc23ae09bf4cac79aeb9ed0a509b6647d2ccf930
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187679"
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


---
title: IEEDataStorage::GetData | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a58f644a71601b16317c4fe63271f4f816da77d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149298"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die angegebene Anzahl von Bytes aus dem Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dataSize`  
 [in] Die Anzahl der abzurufenden Bytes (der `data` Array muss mindestens diese Anzahl von Bytes enthalten).  
  
 `sizeGotten`  
 [out] Gibt die Anzahl der Bytes, die tatsächlich abgerufen.  
  
 `data`  
 [in, out] Ein Array mit den angeforderten Daten gefüllt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die empfohlene Verwendung dieser Methode ist die Datenbytes in ein lokales Array, abrufen, da es keine Möglichkeit, zu der Bytes während des Abfrageprozesses überspringen. In diesem Fall ist der Parameter `dataSize` zurückgegeben werden soll der Wert durch die [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

---
title: 'Idebugarrayobject:: GetDimensions | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09902c60f87cfb92d0f0778fcbd106ade4d8dac4
ms.sourcegitcommit: 9cfd3ef6c65f671a26322320818212a1ed5955fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2019
ms.locfileid: "68197788"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Dimensionen des Arrays ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCount`  
 in Die Anzahl der abzurufenden Dimensionen.  
  
 `dwDimensions`  
 [in, out] Ein Array, das mit den Größen der einzelnen Dimensionen aufgefüllt wird. `dwCount`Gibt die maximale Größe des `dwDimensions` Arrays an.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein mehrdimensionales Array kann für jede Dimension über unterschiedliche Größen verfügen. Bei Angabe des dreidimensionalen Arrays `myarray[3][2][6]`würde diese Methode z. b. 3, 2 und 6 `dwDimensions` im-Parameter in dieser Reihenfolge zurückgeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)

---
title: IDebugArrayObject::GetCount | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4edfaf7b9ef655473244bdcd18bf6b2c31b8210d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891400"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Ruft die Anzahl der Elemente im Array ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwElements`  
 [out] Die Anzahl zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode sieht alle Elemente eines Arrayobjekts als ein eindimensionales Array, selbst wenn das Arrayobjekt mehrdimensionale ist. Angenommen, das Array `myarray[3][2][6]`, 36, die in von dieser Methode zurückgegeben werden würde die `pdwElements` Parameter. Verwenden der [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) Methode, um die einzelnen Elemente einer einzeln ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
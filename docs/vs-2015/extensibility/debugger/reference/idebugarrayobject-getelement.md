---
title: IDebugArrayObject::GetElement | Microsoft-Dokumentation
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
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec19e6c0b3d9e0b73232eda6ea52d674ac1933cf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900604"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft ein Element des Arrays ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwIndex`  
 [in] Der Elementindex.  
  
 `ppElement`  
 [out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle, die das Element darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode sieht alle Elemente eines Arrayobjekts als ein eindimensionales Array, selbst wenn das Arrayobjekt mehrdimensionale ist. Angenommen, das Array `myarray[3][2][6]` und `dwIndex` Parameter von 20, würde dieser Methode das Element aus zurückgeben `myarray[1][1][2]`, und ein `dwIndex` Parameter 21 würde das Element zurückgeben `myarray[1][1][3]`. Verwenden der [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) Methode, um zu bestimmen, die Gesamtanzahl der Elemente im Array.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)


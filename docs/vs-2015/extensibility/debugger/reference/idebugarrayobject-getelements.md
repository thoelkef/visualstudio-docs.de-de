---
title: IDebugArrayObject::GetElements | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16e4ce5b705d55203a0c9b7da02655be91628064
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515857"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugArrayObject::GetElements](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugarrayobject-getelements).  
  
Ruft einen Enumerator aller Elemente des Arrays ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) Objekt, das ermöglicht, über alle Elemente auflisten.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie alternativ die [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) und [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) Methoden zum Durchlaufen der Elemente.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)


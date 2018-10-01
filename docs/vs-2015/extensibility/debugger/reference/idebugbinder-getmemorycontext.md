---
title: IDebugBinder::GetMemoryContext | Microsoft-Dokumentation
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
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e0c9d7dbcd20407d81ccfc7ed0d8f63cdeec974
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523764"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugBinder::GetMemoryContext](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder-getmemorycontext).  
  
Diese Methode konvertiert entweder auf ein Objektspeicherort oder auf eine Speicheradresse, an einen Speicherkontext.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pField`  
 [in] Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , beschreibt das zu suchende Objekt. Wenn `NULL`, verwenden Sie dann `dwConstant` stattdessen.  
  
 `dwConstant`  
 [in] Eine Konstante Speicheradresse, z. B. 0x5000.  
  
 `ppMemCxt`  
 [out] Gibt die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Schnittstelle, die die Adresse des Objekts oder die Adresse im Speicher darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)


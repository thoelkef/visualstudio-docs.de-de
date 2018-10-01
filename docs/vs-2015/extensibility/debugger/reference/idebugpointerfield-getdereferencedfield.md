---
title: IDebugPointerField::GetDereferencedField | Microsoft-Dokumentation
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
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 730f869613341b3733bff47a3bdcb066e987f9a5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511229"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugPointerField::GetDereferencedField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerfield-getdereferencedfield).  
  
Diese Methode gibt den Typ des Objekts, die auf den dieser Zeiger-Objekt verweist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppField`  
 [out] Gibt eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) beschreibt den Typ des Zielobjekts.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn z. B. die [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) -Objekt verweist auf eine ganze Zahl, die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) von dieser Methode zurückgegebene Typ beschreibt, Integer-Datentyp.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)


---
title: IDebugPointerObject::Dereference | Microsoft-Dokumentation
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
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dd1c0652a8c1b165ae37756238c5615c4572c886
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523542"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugPointerObject::Dereference](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerobject-dereference).  
  
Ruft das Objekt, das auf den verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwIndex`  
 [in] Ein einfaches Byteoffset vom Beginn des Objekts verweist.  
  
 `ppObject`  
 [out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt, das Objekt darstellt, auf den verwiesen wird, sowie Werte für offset, sofern vorhanden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn dieses Objekt nicht in ein anderes Objekt verweist.  
  
## <a name="remarks"></a>Hinweise  
 Das Objekt, das auf den verwiesen wird, kann ein primitiver Typ oder ein komplexer Typ wie z. B. eine Klasse oder Struktur sein.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)


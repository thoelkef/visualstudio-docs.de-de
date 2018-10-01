---
title: IDebugField::GetTypeInfo | Microsoft-Dokumentation
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
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc8563b73185e6271329e2c2217a12a4a0e9292c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520403"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugField::GetTypeInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfield-gettypeinfo).  
  
Diese Methode ruft die typunabhängig-Informationen über das Symbol oder einen Typ ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```csharp  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pTypeInfo`  
 [out] Gibt die Typinformationen in der angegebenen [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Typunabhängig Informationen, z. B. gehören der AppDomain, das Modul und Klasse, die das Symbol enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)


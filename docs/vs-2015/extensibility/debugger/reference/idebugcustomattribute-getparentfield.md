---
title: IDebugCustomAttribute::GetParentField | Microsoft-Dokumentation
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
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91b9f94bc40f76c6ff7a0fe4090bca5c89dbd816
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721113"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft das Feld, das an dem das benutzerdefinierte Attribut angefügt ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppField`  
 [out] Gibt die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das Feld darstellt, an dem das benutzerdefinierte Attribut angefügt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) Methode für das zurückgegebene [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, um zu bestimmen, welche Art von das übergeordnete Feld ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)


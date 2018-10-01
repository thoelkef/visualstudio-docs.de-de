---
title: IDebugMethodField::GetGlobalContainer | Microsoft-Dokumentation
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
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aec4171c4e1203c8637e0d03bb7c031442813bf8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514049"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugMethodField::GetGlobalContainer](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmethodfield-getglobalcontainer).  
  
Ruft den globalen Container die Methode ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppClass`  
 [out] Gibt eine [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) für das Modul, in dem diese Methode definiert ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Das zurückgegebene [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt, das gesamte Modul darstellt, und ist ein künstliches Objekt, das heißt, das Modul selbst verfügt nicht über eine tatsächliche Klasse jedoch kann es durch dargestellt werden ein `IDebugClassField` -Objekt, sodass die verschiedenen die Elemente des Moduls aufgelistet und ermittelt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)


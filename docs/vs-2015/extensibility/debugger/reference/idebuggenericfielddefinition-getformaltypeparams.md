---
title: IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3eb40b1b24ca70e0ce1f44490c80231827b5fe1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509774"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugGenericFieldDefinition::GetFormalTypeParams](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams).  
  
Ruft die Typparameter in Anbetracht der Anzahl von Parametern ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```csharp  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cParams`  
 [in] Anzahl von Parametern.  
  
 `ppParams`  
 [out] Ein Array von Typparametern.  
  
 `pcParams`  
 [in, out] Anzahl von Parametern in der `ppParams` Array.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Geben Sie die Typparametern in einer Reihenfolge von links nach rechts. Z. B. Wörterbücher\<K, V > IDebugFormalGenericParameters {K, V} zurückgibt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)


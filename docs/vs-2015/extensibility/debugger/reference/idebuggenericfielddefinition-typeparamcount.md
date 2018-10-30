---
title: IDebugGenericFieldDefinition::TypeParamCount | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 09a220660c6e2ecd9c64d134b70f65c508f08bb2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910770"
---
# <a name="idebuggenericfielddefinitiontypeparamcount"></a>IDebugGenericFieldDefinition::TypeParamCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Anzahl von Typparametern, die dem generischen Feld zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT TypeParamCount(  
   ULONG32* pcParams  
);  
```  
  
```csharp  
int TypeParamCount(  
   ref uint pcParams  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcParams`  
 [in, out] Die Anzahl von Typparametern.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Liste\<T >, diese Methode gibt 1 zurück, und, falls Liste\<T1, T2 >, diese Methode gibt 2 zurück. Diese Methode gibt 0 zurück, wenn keine Typparameter vorhanden sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)


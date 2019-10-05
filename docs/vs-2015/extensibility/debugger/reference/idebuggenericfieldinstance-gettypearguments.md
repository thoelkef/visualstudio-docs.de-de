---
title: IDebugGenericFieldInstance::GetTypeArguments | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bef4d6c0d36eafd0279d97ecad2d1d2cc0656e2c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180830"
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Typargumente für die Parameter für diese Instanz ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetTypeArguments(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   ULONG32*      pcArgs  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint              cArgs,  
   out IDebugField[] ppArgs,  
   ref uint          pcArgs  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cArgs`  
 [in] Die Anzahl von Typparametern.  
  
 `ppArgs`  
 [out] Gibt ein Array von Typparametern.  
  
 `pcArgs`  
 [in, out] Anzahl der Elemente in der `ppArgs` Array.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)

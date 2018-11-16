---
title: IDebugStackFrame2::GetDebugProperty | Microsoft-Dokumentation
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
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c118aadaf21dd935ebaf1d86cfe18322244c53c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800028"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Beschreibung der Eigenschaften des ein Stapelrahmen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppDebugProp  
);  
```  
  
```csharp  
int GetDebugProperty (   
   out IDebugProperty2 ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppDebugProp`  
 [out] Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das die Eigenschaften des Stapelrahmens beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Aufrufen der [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) -Methode mit den entsprechenden Filtern abrufen kann, die lokalen Variablen, Methodenparameter, Register und "this"-Zeigers, die dem Stapelrahmen zugeordnet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)


---
title: IDebugMethodField::EnumParameters | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 112b91c2155c28b37b2222a99a45893fcb56e98c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122196"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Erstellt einen Enumerator für die Parameter der Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppParams`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der Parameter der Methode darstellt; andernfalls wird einen null-Wert zurückgegeben, wenn keine Parameter vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei Erfolg S_OK zurückgibt, oder gibt "S_FALSE" zurück, wenn keine Parameter vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jedes Element ist ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, das verschiedene Typen von Parametern darstellt. Rufen Sie die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) -Methode für jedes Objekt, um zu bestimmen, genau welche Art von Parameter für das Objekt darstellt.  
  
 Enthält einen Parameter, dessen Variablenname und ihren Typ gleichzeitig. Der erste Parameter an eine Klassenmethode ist in der Regel der "this" Zeiger.  
  
 Wenn nur die Typen der Parameter erforderlich ist, rufen die [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
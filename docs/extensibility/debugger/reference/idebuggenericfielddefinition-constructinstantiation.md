---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f72e251f66c196ec36eb68f5a228536658ab89d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823942"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Erstellt eine Feldinstanz, die ein Array von Typargumenten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cArgs`  
 [in] Anzahl der Argumente in der `ppArgs` Array.  
  
 `ppArgs`  
 [in] Ein Array, das die Typargumente enthält. Die Typargumente müssen es sich um geschlossene Typen (Generika nicht generisch oder vollständig instanziiert) sein.  
  
 `ppConstructedField`  
 [out] Gibt die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, die das neue Feld darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Einschränkungen werden nicht überprüft.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
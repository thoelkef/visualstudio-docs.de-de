---
title: IDebugAlias::GetICorDebugValue | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38debf5be309a97367f9a14c5f07ec3db6e7b666
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005942"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Ruft ab eine verwaltete Codeschnittstelle, die den Wert dieser Alias darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppUnk`  
 [out] `IUnknown` Schnittstelle, die den Wert dieser Alias darstellt. Diese Schnittstelle abgefragt werden kann, für die `ICorDebugValue` Schnittstelle.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gilt nur für verwaltete Werte (die `ICorDebugValue` steht eine Schnittstelle in der [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] und in der [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] -SDK in der Datei "cordebug.idl").  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
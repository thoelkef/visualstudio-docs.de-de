---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4e23641f246d064dc65c01788bdfb780c0f09869
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Ruft ab eine verwaltete Codeschnittstelle, die den zugeordneten Wert durch diesen Alias darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppUnk`  
 [out] `IUnknown` Schnittstelle, die den zugeordneten Wert durch diesen Alias darstellt. Diese Schnittstelle kann abgefragt werden, für die `ICorDebugValue` Schnittstelle.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gilt nur für verwaltete Werte (die `ICorDebugValue` steht eine Schnittstelle in der [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] und in der [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK in die Datei "cordebug.idl").  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
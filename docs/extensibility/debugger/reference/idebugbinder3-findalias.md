---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b88ae0da5f90da45d33ec56169665e9c8430846c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Diese Methode sucht einen Alias, erhält einen Namen an. Dadurch werden alle Aliase im Programm suchen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcstrName`  
 [in] Der Name des Alias gefunden.  
  
 `ppAlias`  
 [out] Alias gefunden (sofern vorhanden) dargestellt wird, indem die [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) Schnittstelle.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` (wenn der Alias nicht gefunden wird) oder ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode initialisiert das Zielobjekt, vor dem Aufruf null; testet dann null-Werte anschließend, um zu bestimmen, und zwar unabhängig davon, ob der Alias gefunden wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
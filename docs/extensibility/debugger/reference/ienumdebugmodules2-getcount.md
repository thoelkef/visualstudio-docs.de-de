---
title: IEnumDebugModules2::GetCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugModules2::GetCount
helpviewer_keywords: IEnumDebugModules2::GetCount
ms.assetid: f4def3d2-7cc9-4cd2-9649-3b7e00a76220
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0ca1c7c9c40c1a3645ad35131caac51184b4f66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugmodules2getcount"></a>IEnumDebugModules2::GetCount
Gibt die Anzahl der Elemente in der Enumeration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcelt`  
 [out] Gibt die Anzahl der Elemente in der Enumeration zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist nicht Teil der üblichen COM-Enumerationsschnittstelle, die angibt, dass nur die `Next`, `Clone`, `Skip`, und `Reset` Methoden implementiert werden müssen.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
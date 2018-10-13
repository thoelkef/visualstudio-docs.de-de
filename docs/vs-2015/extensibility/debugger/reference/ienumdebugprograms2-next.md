---
title: IEnumDebugPrograms2::Next | Microsoft-Dokumentation
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
- IEnumDebugPrograms2::Next
helpviewer_keywords:
- IEnumDebugPrograms2::Next
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 921965a9e761ffbc890467a8a25e4650471b82eb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237665"
---
# <a name="ienumdebugprograms2next"></a>IEnumDebugPrograms2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den nächsten Satz von Elementen aus der Enumeration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Next(  
   ULONG            celt,  
   IDebugProgram2** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint             celt,  
   IDebugProgram2[] rgelt,  
   ref uint         pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale Größe der `rgelt` Array.  
  
 `rgelt`  
 [in, out] Array von [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Elementen gefüllt werden soll.  
  
 `pceltFetched`  
 [out] Gibt die Anzahl der im tatsächlich zurückgegebenen Elemente `rgelt`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden können; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)


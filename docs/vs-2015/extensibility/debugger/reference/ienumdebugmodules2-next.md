---
title: IEnumDebugModules2::Next | Microsoft-Dokumentation
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
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de3e9d029a8d51f61c83ef81444116af83e64e8e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282216"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den nächsten Satz von Elementen aus der Enumeration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Next(  
   ULONG           celt,  
   IDebugModule2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugModule2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der abzurufenden Elemente. Gibt auch die maximale Größe der `rgelt` Array.  
  
 `rgelt`  
 [in, out] Array von [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) Elementen gefüllt werden soll.  
  
 `pceltFetched`  
 [out] Gibt die Anzahl der im tatsächlich zurückgegebenen Elemente `rgelt`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden können; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)


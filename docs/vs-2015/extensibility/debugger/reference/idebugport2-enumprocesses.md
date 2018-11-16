---
title: IDebugPort2::EnumProcesses | Microsoft-Dokumentation
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
- IDebugPort2::EnumProcesses
helpviewer_keywords:
- IDebugPort2::EnumProcesses
ms.assetid: aafb32c5-5790-4807-a448-878a80256438
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15c8939fa7c220592620213ba837c5e8a76bd5f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732782"
---
# <a name="idebugport2enumprocesses"></a>IDebugPort2::EnumProcesses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt eine Liste aller Prozesse, die auf einem Port ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumProcesses(   
   IEnumDebugProcesses2** ppEnum  
);  
```  
  
```csharp  
int EnumProcesses(   
   out IEnumDebugProcesses2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md) -Objekt, das eine Liste aller Prozesse, die an einen Port enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)


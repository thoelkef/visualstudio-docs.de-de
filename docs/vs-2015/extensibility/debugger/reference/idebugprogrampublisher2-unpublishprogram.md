---
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 05efc566cec0e7e885b16a4bb7c7e7d6256ac7b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146281"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wird ein Programm nicht verfügbar, die debuggt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pDebuggeeInterface`  
 [in] Ein `IUnknown` Schnittstelle, um die Anwendung. Dies ist der gleiche Wert angegeben die [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) Methode und eindeutig identifiziert die Anwendung entfernt wird (d. h., er dient als ein Cookie).  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Um ein Programm auf die Debug-Engines und sitzungsbasierter Debug-Manager verfügbar zu machen, verwenden Sie die [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)

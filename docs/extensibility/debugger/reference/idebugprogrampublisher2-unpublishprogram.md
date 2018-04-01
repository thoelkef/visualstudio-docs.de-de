---
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 14fd0c09d9a654e8d8ff7097a8974142f0317901
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Stellt ein Programm, das gedebuggt werden nicht verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pDebuggeeInterface`  
 [in] Ein `IUnknown` Schnittstelle, um das Programm. Dies stimmt mit dem bereitgestellten Wert der [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) Methode und eindeutig identifiziert die Anwendung entfernt wird (d. h., es dient als Cookie).  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Um ein Programm auf den Debugmodule und die Sitzung Debug-Manager verfügbar zu machen, verwenden Sie die [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
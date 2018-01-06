---
title: IDebugProgram2::GetProgramId | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetProgramId
helpviewer_keywords: IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5edf51bfa37cfdca7779417cd01320a1ee89cbd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Ruft eine GUID für dieses Programm an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```csharp  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pguidProgramId`  
 [out] Gibt die `GUID` für dieses Programm.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Debugging-Modul (DE) muss den Programmbezeichner, der ursprünglich übergeben Zurückgeben der [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) oder [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methoden. Dies ermöglicht die Identifikation des Programms über Debugger Komponenten.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
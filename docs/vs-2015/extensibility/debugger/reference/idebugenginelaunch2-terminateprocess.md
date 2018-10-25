---
title: IDebugEngineLaunch2::TerminateProcess | Microsoft-Dokumentation
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
- IDebugEngineLaunch2::TerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::TerminateProcess
ms.assetid: f7039e7f-5f57-4222-9ad2-11a66b2da6e0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d50acb35d1b1ecba539d33539fbde91c4db2082
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862840"
---
# <a name="idebugenginelaunch2terminateprocess"></a>IDebugEngineLaunch2::TerminateProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beendet einen Prozess an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT TerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```csharp  
int TerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pProcess`  
 [in] Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Objekt, das den Prozess zu beendenden darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie die [CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md) Methode vor dem Aufrufen dieser Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)


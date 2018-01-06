---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: af2f9e5851e53c86fb5466e7fc2cdfe515b5fb21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
ALS VERALTET MARKIERT. DARF NICHT VERWENDET WERDEN.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Implementierung sollte stets `E_NOTIMPL`.  
  
## <a name="remarks"></a>Hinweise  
  
> [!WARNING]
>  Als der [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], diese Methode wird nicht mehr verwendet und sollten stets `E_NOTIMPL`.  
  
 Diese Methode wird aufgerufen, wenn der Debugger unerwartet beendet wird. Wenn diese Methode aufgerufen wird, sollte DE das Programm fortgesetzt, als ob der Benutzer von ihm getrennt. Keine weiteren Debuggingereignisse gesendet werden soll. Das Programm sollte sich in einem Zustand, wo es von einer anderen Instanz des Debuggers anfügbar ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
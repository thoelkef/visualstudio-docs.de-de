---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft-Dokumentation
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
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 271a4053d90efd2d852e8b67ae8ad4d4353afa37
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822306"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ALS VERALTET MARKIERT. VERWENDEN SIE NICHT.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Implementierung sollte immer zurückgeben `E_NOTIMPL`.  
  
## <a name="remarks"></a>Hinweise  
  
> [!WARNING]
>  Als [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], diese Methode wird nicht mehr verwendet und sollte immer zurückgeben `E_NOTIMPL`.  
  
 Diese Methode wird aufgerufen, wenn der Debugger unerwartet beendet wird. Wenn diese Methode aufgerufen wird, sollte die DE das Programm fortgesetzt, als ob der Benutzer von ihm getrennt. Keine weiteren Debuggingereignisse gesendet werden soll. Das Programm sollte sich in einem Zustand, in denen es anfügbaren Member aus einer anderen Instanz des Debuggers ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)


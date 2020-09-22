---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c60bc42895a0527f1638dada5a28a1631314e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841055"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Veraltet. Verwenden Sie nicht.  
  
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
 Eine-Implementierung sollte immer zurückgeben `E_NOTIMPL` .  
  
## <a name="remarks"></a>Bemerkungen  
  
> [!WARNING]
> Ab [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] wird diese Methode nicht mehr verwendet und sollte immer zurückgeben `E_NOTIMPL` .  
  
 Diese Methode wird aufgerufen, wenn der Debugger unerwartet beendet wird. Wenn diese Methode aufgerufen wird, sollte die de das Programm so fortsetzen, als wäre der Benutzer von ihm getrennt. Es sollten keine weiteren Debuggingereignisse gesendet werden. Das Programm sollte sich in einem Zustand befinden, in dem er von einer anderen Instanz des Debuggers angehängt werden kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

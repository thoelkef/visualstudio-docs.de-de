---
title: IDebugProgram2::CauseBreak | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a1bfd8c2094c6ef9d961eb5375aae7cf5c6d13da
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511916"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProgram2::CauseBreak](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-causebreak).  
  
Fordert an, dass das Programm die Ausführung der nächsten beenden Zeitpunkt eins seiner Threads Versuche ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) Ereignis wird immer dann gesendet, wenn Sie als Nächstes versucht das Programm, um Code auszuführen, nachdem diese Methode aufgerufen wird.  
  
 Diese Methode ist asynchron, darin, dass die Methode sofort zurückgegeben, ohne dass unbedingt zum Beenden des Programms.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)


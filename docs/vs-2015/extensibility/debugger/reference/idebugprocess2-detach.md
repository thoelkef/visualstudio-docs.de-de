---
title: IDebugProcess2::Detach | Microsoft-Dokumentation
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
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1895c146f557e0c3ba79bd84970b99fc663cc891
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515480"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProcess2::Detach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess2-detach).  
  
Trennt den Debugger von diesem Prozess, indem Sie alle Programme im Prozess trennen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Alle Programme und der Prozess weiter ausgeführt, aber sind nicht mehr Teil der Debugsitzung. Nachdem der Trennvorgang abgeschlossen ist, nicht mehr Debuggen, die Ereignisse für diesen Prozess (und seine Programme) gesendet werden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)


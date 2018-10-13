---
title: IDebugCoreServer3::QueryIsLocal | Microsoft-Dokumentation
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
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6cebb27caceca5dd743fbe777092eaee6b2ec966
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180699"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob der Server an den Aufrufer lokal ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` an der Server lokal ist. Gibt `S_FALSE` , wenn der Server von einer Instanz von msvsmon.exe, ausgeführt wird, die in der Regel für das Remotedebugging verwendet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)


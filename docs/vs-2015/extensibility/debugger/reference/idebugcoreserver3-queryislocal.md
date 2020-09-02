---
title: 'IDebugCoreServer3:: queryislocal | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 26bed2a60d7412682588a5a39fd6f1301005da01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569080"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob der Server für den Aufrufer lokal ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt zurück `S_OK` , um anzugeben, dass der Server lokal ist. Gibt zurück `S_FALSE` , wenn der Server von einer Instanz von msvsmon.exe ausgeführt wird, die in der Regel für das Remote Debuggen verwendet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)

---
title: 'IDebugPortEx2:: TerminateProcess | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2::TerminateProcess
helpviewer_keywords:
- IDebugPortEx2::TerminateProcess
ms.assetid: bf8fa94c-6d9d-4e4f-ac08-3b44ba5ace68
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8e524ac03b11eeee540c32af07fa422f83a7ac6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188437"
---
# <a name="idebugportex2terminateprocess"></a>IDebugPortEx2::TerminateProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beendet einen Prozess.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT TerminateProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```csharp  
int TerminateProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pPortProcess`  
 in Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) -Objekt, das den zu beendenden Prozess darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

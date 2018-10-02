---
title: IDebugEngine2::RemoveSetException | Microsoft-Dokumentation
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
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e68d7420fa89e18b86ed7c2fda8633f2c2703b9b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516348"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugEngine2::RemoveSetException](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine2-removesetexception).  
  
Entfernt die angegebene Ausnahme an, damit sie nicht mehr von der Debug-Engine verarbeitet wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT RemoveSetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int RemoveSetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pException`  
 [in] Ein [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) -Struktur, die die Ausnahme zu entfernenden beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Ausnahme, die entfernt werden muss zuvor festgelegt wurden durch einen früheren Aufruf von der [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) Methode.  
  
 Um alle Ausnahmen, die Gruppe auf einmal entfernen, rufen die [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)


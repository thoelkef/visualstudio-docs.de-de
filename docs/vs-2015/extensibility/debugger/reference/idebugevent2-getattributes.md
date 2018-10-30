---
title: IDebugEvent2::GetAttributes | Microsoft-Dokumentation
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
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fde5fc207416782576252148a6abcf218ea0bc78
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841714"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Attribute für dieses Ereignis Debuggen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```csharp  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwAttrib`  
 [out] Eine Kombination von Flags aus der [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) Enumeration.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle ist für alle Ereignisse. Diese Methode beschreibt den Typ des Ereignisses; Beispielsweise ist das Ereignis, synchron oder asynchron, und ist es eine Beenden-Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)


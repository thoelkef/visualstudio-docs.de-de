---
title: IDebugPortSupplier2::CanAddPort | Microsoft-Dokumentation
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
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1478841e6fdd48a6c956486153db7bf4e81435fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509271"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugPortSupplier2::CanAddPort](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplier2-canaddport).  
  
Stellt sicher, dass ein portanbieters neue Ports hinzufügen kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt zurück, wenn der Port hinzugefügt werden kann, `S_OK`ist, andernfalls gibt `S_FALSE` an, dass keine Ports können diese anschlusslieferant hinzugefügt werden.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie diese Methode vor dem Aufruf der [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) Methode, da die zweite Methode erstellt, den Port sowie das Hinzufügen, die möglicherweise einen zeitaufwändigen Vorgang.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)


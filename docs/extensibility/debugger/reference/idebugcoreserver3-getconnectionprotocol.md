---
title: IDebugCoreServer3::GetConnectionProtocol | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::GetConnectionProtocol
helpviewer_keywords:
- IDebugCoreServer3::GetConnectionProtocol
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 8901f9fff01ecdfe21e3731df8b2d155fe250ac2
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# IDebugCoreServer3::GetConnectionProtocol
Gibt einen Wert, der angibt, des Protokolls, das für die Kommunikation zwischen dem Server und das debugpaket verwendet wird.  
  
## Syntax  
  
```cpp  
HRESULT GetConnectionProtocol(  
   CONNECTION_PROTOCOL* pProtocol  
);  
```  
  
```csharp  
int GetConnectionProtocol(  
   CONNECTION_PROTOCOL[] pProtocol  
);  
```  
  
#### Parameter  
 `pProtocol`  
 [out] Gibt einen der Werte aus den [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) Enumeration.  
  
## Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)

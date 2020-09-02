---
title: 'IDebugPortSupplier2:: canaddport | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4ec078650446d3511ed9c5bdc8ee3ec0191487d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188349"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hiermit wird überprüft, ob ein Port Lieferant neue Ports hinzufügen kann.  
  
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
 Wenn der Port hinzugefügt werden kann, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben, `S_FALSE` um anzugeben, dass diesem Port Lieferanten keine Ports hinzugefügt werden können.  
  
## <a name="remarks"></a>Bemerkungen  
 Rufen Sie diese Methode auf, bevor Sie die [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) -Methode aufrufen, da die zweite Methode den Port erstellt und hinzugefügt wird, was möglicherweise ein zeitaufwendiger Vorgang ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

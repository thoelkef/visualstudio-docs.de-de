---
title: 'IDebugBinder3:: getmemoryobject | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0019b1691cb36b9d23be546cdfdb0e061779647d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193023"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft ein Speicher Objekt ab, das den Speicher darstellt, an den dieses Objekt gebunden ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetMemoryObject(  
   IDebugField*   pField,  
   UINT64         uConstant,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetMemoryObject(  
   IDebugField      pField,  
   long             uConstant,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pField`  
 in Gibt an, für welches Feld das Speicher Objekt zu erhalten ist.  
  
 `uConstant`  
 in Stellt eine Speicheradresse oder einen Wert für einen konstanten Wert dar.  
  
 `ppObject`  
 vorgenommen Ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, das den Speicher darstellt, an den dieses Objekt gebunden ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

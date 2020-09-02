---
title: 'Idebugbinder:: Bind | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 547f94cb4534bcb281cce0fdc2ff7db5fefe3593
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423542"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft den Arbeitsspeicher Kontext oder das Objekt ab, das den aktuellen Wert des Symbols enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pContainer`  
 in Das [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) , das das untergeordnete Element enthält, auf das verweist `pField` .  
  
 `pField`  
 in Das [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) , das das Symbol darstellt.  
  
 `ppObject`  
 vorgenommen Gibt den zurück `IDebugObject` , der die Instanz des Symbols darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

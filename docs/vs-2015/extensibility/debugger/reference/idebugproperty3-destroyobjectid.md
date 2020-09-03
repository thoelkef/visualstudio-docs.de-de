---
title: IDebugProperty3::D estroyobjectid | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a610cd5c947d77048e86b31c92298f6cc18607d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193425"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zerstört die eindeutige ID, die dieser Eigenschaft zugeordnet ist, und gibt an, dass der Aufrufer nicht mehr interessiert ist, diese Eigenschaft eindeutig aus allen anderen Eigenschaften zu identifizieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die Debug-Engine eindeutige IDs für eine Eigenschaft nicht unterstützen muss (weil Sie diese bereits eindeutig nachverfolgt), kann Sie einfach `E_NOTIMPL` für diese Methode zurückgeben.  
  
 Eindeutige IDs werden mit einem Aufruf der Methode " [kreateobjectid](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) " erstellt, wenn der Aufrufer sicherstellen möchte, dass diese Eigenschaft unter allen anderen Eigenschaften eindeutig identifiziert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)

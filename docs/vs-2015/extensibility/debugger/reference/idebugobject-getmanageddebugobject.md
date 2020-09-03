---
title: 'Idebugobject:: getmanageddebugobject | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4f2917135f5e25648cf08cd9030e3fdf31aedb52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162473"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt eine Kopie des verwalteten Objekts im Adressraum der Debug-Engine.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppObject`  
 vorgenommen Gibt ein [idebugmanagedobject](../../../extensibility/debugger/reference/idebugmanagedobject.md) -Objekt zurück, das das neu erstellte verwaltete-Objekt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) keine Instanz einer verwalteten Wert Klasse darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt muss eine Instanz der verwalteten Wert Klasse, z. b. eine-Instanz, darstellen `System.Decimal` . Wenn eine lokale Kopie vorhanden ist, wird der Aufwand für das Aufrufen von [Evaluierungen](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) vermieden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

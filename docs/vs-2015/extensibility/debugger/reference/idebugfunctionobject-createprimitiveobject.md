---
title: 'Idebugfunctionobject:: erkreateprimitiveobject | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3531483c113c37587b253bed90a9985541b2e526
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179442"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt ein Primitives Datenobjekt, z. b. eine einfache Ganzzahl.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ot`  
 in Ein Wert aus der [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) Enumeration, die den Typ des zu erstellenden primitiven darstellt.  
  
 `ppObject`  
 vorgenommen Gibt ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt zurück, das das neu erstellte-Objekt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das ein Primitives Objekt darstellt, das ein Parameter für die Funktion ist, die durch die [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle dargestellt wird. Wenn die Ausdrucks Zeichenfolge z. b. "myString (5)" lautet, wird diese Methode verwendet, um ein Objekt zu erstellen, das die Ganzzahl 5 darstellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

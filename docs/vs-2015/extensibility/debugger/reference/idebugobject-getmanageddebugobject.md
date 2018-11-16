---
title: IDebugObject::GetManagedDebugObject | Microsoft-Dokumentation
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
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5530865b9d6c7cfb74c91f00b6a65e41702135cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807269"
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
 [out] Gibt eine [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) Objekt, das das neu erstellte verwaltete Objekt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn diese [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) stellt keine Instanz einer verwalteten Klasse dar.  
  
## <a name="remarks"></a>Hinweise  
 Dies [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt muss eine Klasseninstanz verwalteten Wert darstellen, z. B. eine `System.Decimal` Instanz. Indem Sie eine lokale Kopie, den Aufwand des Aufrufs [auswerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) wird gelöscht.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)


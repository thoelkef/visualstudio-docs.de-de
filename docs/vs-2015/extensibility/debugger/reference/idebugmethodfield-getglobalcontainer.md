---
title: 'Idebugmethodfield:: getglobalcontainer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63912b75435de503dec677b715d1914b419ba07a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162569"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den globalen Container der Methode ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppClass`  
 vorgenommen Gibt ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) zurück, das das Modul darstellt, in dem diese Methode definiert ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Das zurückgegebene [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt stellt das gesamte Modul dar und ist ein künstliches Objekt, d. h., das Modul selbst hat keine tatsächliche Klasse, kann jedoch durch ein Objekt dargestellt werden `IDebugClassField` , sodass die verschiedenen Elemente des Moduls aufgezählt und ermittelt werden können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

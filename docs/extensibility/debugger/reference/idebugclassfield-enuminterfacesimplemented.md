---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da72bcbe32a4de2760d7b42a580c0550b5cfa17f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944734"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Erstellt einen Enumerator für die von dieser Klasse implementierten Schnittstellen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der implementierten Schnittstellen darstellt. Gibt einen null-Wert zurück, wenn keine Schnittstellen vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn keine Schnittstellen implementiert, die für diese Klasse vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jedes Element der Enumeration ist ein [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt, das eine Schnittstelle beschreibt. Beachten Sie, die nicht verwaltete [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Code verwendet keine Schnittstellen als diskrete Entität, damit diese Methode immer einen null-Wert gibt für nicht verwaltete [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Code.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
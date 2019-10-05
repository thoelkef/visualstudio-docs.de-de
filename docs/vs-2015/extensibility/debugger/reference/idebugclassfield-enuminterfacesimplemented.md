---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45cdc4ea3d1dad911179ce7b2a4926248ee921fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191016"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator für die von dieser Klasse implementierten Schnittstellen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Jedes Element der Enumeration ist ein [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt, das eine Schnittstelle beschreibt. Beachten Sie, die nicht verwaltete [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] Code verwendet keine Schnittstellen als diskrete Entität, damit diese Methode immer einen null-Wert gibt für nicht verwaltete [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] Code.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)

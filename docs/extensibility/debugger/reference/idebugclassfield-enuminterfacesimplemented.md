---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a1de38344b8570df0b5381842be508e45c5fdb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203202"
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

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der implementierten Schnittstellen darstellt. Gibt einen null-Wert zurück, wenn keine Schnittstellen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn keine Schnittstellen implementiert, die für diese Klasse vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Jedes Element der Enumeration ist ein [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt, das eine Schnittstelle beschreibt. Beachten Sie, die nicht verwaltete [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Code verwendet keine Schnittstellen als diskrete Entität, damit diese Methode immer einen null-Wert gibt für nicht verwaltete [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Code.

## <a name="see-also"></a>Siehe auch
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
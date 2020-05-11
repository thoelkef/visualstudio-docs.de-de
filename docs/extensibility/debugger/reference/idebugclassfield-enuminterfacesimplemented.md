---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734490"
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
[out] Gibt ein [IEnumDebugFields-Objekt](../../../extensibility/debugger/reference/ienumdebugfields.md) zurück, das die Liste der implementierten Schnittstellen darstellt. Gibt einen NULL-Wert zurück, wenn keine Schnittstellen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn für diese Klasse keine Schnittstellen implementiert sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jedes Element der Enumeration ist ein [IDebugClassField-Objekt,](../../../extensibility/debugger/reference/idebugclassfield.md) das eine Schnittstelle beschreibt. Beachten Sie, [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] dass nicht verwalteter Code Schnittstellen nicht als diskrete Entität verwendet, sodass diese Methode immer einen NULL-Wert für nicht verwalteten [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] Code zurückgibt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)

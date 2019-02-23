---
title: IDebugClassField::DoesInterfaceExist | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7884bff62321ed07c3a11a6db65855b1edea0adc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688406"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Bestimmt, ob eine bestimmte Schnittstelle in der Klasse definiert ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

#### <a name="parameters"></a>Parameter
 `pszInterfaceName`

 [in] Eine Zeichenfolge, die den schnittstellenamen enthält, der gesucht wird.

## <a name="return-value"></a>Rückgabewert
 Bei Erfolg S_OK zurückgibt, gibt S_FALSE zurück, wenn die Schnittstelle nicht vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode ruft eine Enumeration aller Schnittstellen in Kraft und durchsucht die Liste für die entsprechende Schnittstelle.

## <a name="see-also"></a>Siehe auch
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
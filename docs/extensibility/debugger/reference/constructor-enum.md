---
title: CONSTRUCTOR_ENUM | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd5067591f4f296825db6362f4a7b91f1a7a37e8
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412811"
---
# <a name="constructorenum"></a>CONSTRUCTOR_ENUM
Wählt aus verschiedenen Arten von Konstruktoren.

## <a name="syntax"></a>Syntax

```cpp
typedef enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
} CONSTRUCTOR_ENUM;
```

```csharp
public enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
};
```

## <a name="members"></a>Member
crAll  
Wählt alle Konstruktoren aus.

crNonStatic  
Wählt die nicht statische Konstruktoren.

crStatic  
Wählt aus statische Konstruktoren.

## <a name="remarks"></a>Hinweise
Übergeben als Argument an die [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)

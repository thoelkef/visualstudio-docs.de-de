---
title: DisplayKind | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 152f3b501aad6bba9e87e861346fa9ddb876a44d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315624"
---
# <a name="displaykind"></a>DisplayKind
Listet die gültigen Werte, die darstellen, die Arten von Informationen aus einer [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) -Objekt und dem Benutzer anzuzeigen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
typedef DWORD DisplayKind;
```

```csharp
public enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
```

#### <a name="parameters"></a>Parameter
DisplayKind_Value  
Der Wert des Felds.

DisplayKind_Name  
Der Name des Felds.

DisplayKind_Type  
Typ des Felds.

## <a name="requirements"></a>Anforderungen
Header: EE.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)

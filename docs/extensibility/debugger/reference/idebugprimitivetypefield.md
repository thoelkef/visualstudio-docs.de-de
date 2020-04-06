---
title: IDebugPrimitiveTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07cd3d1a1f80d1c5e816877b7e70a9e65d24d650
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724268"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Stellt einen primitiven Typenumerationswert aus einer [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) dar.

## <a name="syntax"></a>Syntax

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden auf der [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Ruft den primitiven Typ ab, der diesem Feld zugeordnet ist.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

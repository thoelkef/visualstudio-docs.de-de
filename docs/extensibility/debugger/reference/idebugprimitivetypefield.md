---
title: IDebugPrimitiveTypeField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4012b919cffc5e16433567fac283ac731d4d215c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353277"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Stellt einen primitiven Typ Enumeration-Wert aus einer [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle.

## <a name="syntax"></a>Syntax

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, die diese Schnittstelle implementiert, die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Ruft ab, der primitive Typ, der diesem Feld zugeordnet.|

## <a name="requirements"></a>Anforderungen
 Header: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
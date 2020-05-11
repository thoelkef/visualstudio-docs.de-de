---
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b04b0805aec5ecee818fa42e1d76a76cce12b66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727843"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Stellt einen Parameter für einen generischen Codetyp für verwalteten Code dar.

## <a name="syntax"></a>Syntax

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Wird zur Unterstützung von Generika verwendet.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden auf der [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Gibt die Anzahl der Einschränkungen zurück, die diesem generischen Parameter zugeordnet sind.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Ruft die Einschränkungen ab, die diesem generischen Parameter zugeordnet sind.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Ruft die Flags für diesen generischen Parameter ab.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Ruft den Index dieses generischen Parameters ab.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Ruft den Namen dieses generischen Parameters ab.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Ruft den Typ oder Methodenbesitzer dieses generischen Parameters ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

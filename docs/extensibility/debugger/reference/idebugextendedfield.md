---
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad10050aa157b4481fa2041ec5f322451983149f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729040"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Erweitert die Feldtypen, die zur Unterstützung von generischem Code verfügbar sind.

## <a name="syntax"></a>Syntax

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden auf der [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Ruft die angegebene erweiterte Feldart ab.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Legt fest, ob das Feld einen geschlossenen Typ darstellt.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

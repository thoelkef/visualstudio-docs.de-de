---
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed34284e373a7d96761aabe5a7f179367649bc0f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718299"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Erweitert den **IDebugTypeFieldBuilder,** um Arraytypen erstellen zu können.

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle kann vom Symbolanbieter bezogen werden.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden auf der [IDebugTypeFieldBuilder-Schnittstelle](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Erstellt ein Array des angegebenen Typs und der angegebenen Größe.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

---
title: IDebugTypeFieldBuilder2 | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718299"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Erweitert den **idebugtypefieldbuilder** , damit Array Typen erstellt werden können.

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle kann vom Symbol Anbieter abgerufen werden.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden in der [idebugtypefieldbuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) -Schnittstelle implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Erstellt ein Array des angegebenen Typs und der angegebenen Größe.|

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

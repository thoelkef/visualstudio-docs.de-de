---
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e142ed1229f59cfc22ff33cba48e9e35eb4e4406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726975"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Stellt einen optionalen Debugmodifizierer dar.

## <a name="syntax"></a>Syntax

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Von einem [IDebugField-Objekt](../../../extensibility/debugger/reference/idebugfield.md) abgerufen, das eine Klasse oder Methode darstellt.

## <a name="methods"></a>Methoden
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Ruft eine Liste optionaler Modifikatoren ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

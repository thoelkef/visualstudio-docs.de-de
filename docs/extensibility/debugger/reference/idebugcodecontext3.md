---
title: IDebugCodeContext3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734186"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Erweitert die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Schnittstelle, um das Abrufen von Modul-und Prozessschnittstellen zu ermöglichen.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Wird von Debug-engines implementiert und vom [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugpaket verwendet.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden der- `IDebugCodeContext2` Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Ruft einen Verweis auf die-Schnittstelle des Debug-Moduls ab.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Ruft einen Verweis auf die-Schnittstelle des Debugprozesses ab.|

## <a name="remarks"></a>Bemerkungen
 Dies ist eine optionale Schnittstelle, die in der Regel nicht implementiert werden muss.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

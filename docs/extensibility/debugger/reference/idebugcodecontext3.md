---
title: IDebugCodeContext3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db3b27e510ccdbb5ec55c5bfae373114df0c9b16
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338973"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Erweitert die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Schnittstelle für den Abruf von Modul und die Prozess-Schnittstellen zu aktivieren.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Von der Debug-Engines implementiert und von der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] -Paket debuggen.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die `IDebugCodeContext2` Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Ruft einen Verweis auf die Schnittstelle von der Debug-Modul ab.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Ruft einen Verweis auf die Schnittstelle von der Debug-Prozess ab.|

## <a name="remarks"></a>Hinweise
 Dies ist eine optionale Schnittstelle, die in der Regel nicht unbedingt implementiert werden.

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
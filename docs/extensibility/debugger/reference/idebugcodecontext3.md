---
title: IDebugCodeContext3 | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734186"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Erweitert die [IDebugCodeContext2-Schnittstelle,](../../../extensibility/debugger/reference/idebugcodecontext2.md) um das Abrufen von Modul- und Prozessschnittstellen zu ermöglichen.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Wird von Debug-Engines [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementiert und vom Debugpaket verbraucht.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden `IDebugCodeContext2` auf der Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Getmodule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Ruft einen Verweis auf die Schnittstelle des Debugmoduls ab.|
|[Getprocess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Ruft einen Verweis auf die Schnittstelle des Debugprozesses ab.|

## <a name="remarks"></a>Bemerkungen
 Dies ist eine optionale Schnittstelle, die in der Regel nicht implementiert werden muss.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

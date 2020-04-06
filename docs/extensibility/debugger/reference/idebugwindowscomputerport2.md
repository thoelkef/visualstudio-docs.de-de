---
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ef4162469651e4b69502d3a9639d1e86c62e0b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718228"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Ermöglicht abfragen nach Informationen über den Zielcomputer.

## <a name="syntax"></a>Syntax

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Portobjekten des Sitzungsdebug-Managers implementiert.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt `IDebugWindowsComputerPort2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Ruft Informationen über den Computer ab, auf dem der Debugger ausgeführt wird.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

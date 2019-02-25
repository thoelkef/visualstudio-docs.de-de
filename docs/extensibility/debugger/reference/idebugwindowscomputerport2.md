---
title: IDebugWindowsComputerPort2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9126d7507f47852b7fc9bcd3777b112932892bb4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702147"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Ermöglicht das Abfragen von Informationen über den Zielcomputer.

## <a name="syntax"></a>Syntax

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Port-Objekten, von der Sitzungs-Manager implementiert.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt die Methoden der `IDebugWindowsComputerPort2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Ruft Informationen über den Computer, auf denen der Debugger in ausgeführt wird.|

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
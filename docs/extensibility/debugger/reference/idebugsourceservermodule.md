---
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2c362bc4a103c707238acfa3b3148f00c0e25be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719908"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Stellt die Quellserverinformationen dar, die in einer PDB-Datei enthalten sind.

## <a name="syntax"></a>Syntax

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Debugger-Engines implementiert und von der Debugger-Benutzeroberfläche verwendet.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt `IDebugSourceServerModule`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Ruft ein Array von Quellserverinformationen ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

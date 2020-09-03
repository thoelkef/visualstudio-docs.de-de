---
title: Idebugsourceservermodule | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719908"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Stellt die Quell Server Informationen dar, die in einer PDB-Datei enthalten sind.

## <a name="syntax"></a>Syntax

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Debugger-Engines implementiert und von der Debugger-Benutzeroberfläche genutzt.

## <a name="methods"></a>Methoden
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugSourceServerModule` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Ruft ein Array von Quell Server Informationen ab.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

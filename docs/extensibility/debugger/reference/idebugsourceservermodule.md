---
title: IDebugSourceServerModule | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5bb686ff492ca836d35b21d54298876314ecb8d5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321914"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Stellt die Source Server-Informationen, die in einer PDB-Datei enthalten ist.

## <a name="syntax"></a>Syntax

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird vom Debugger-Engines implementiert und genutzt werden, indem Sie die Debugger-Benutzeroberfläche.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt die Methoden der `IDebugSourceServerModule`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Ruft ein Array von Quellserverinformationen ab.|

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
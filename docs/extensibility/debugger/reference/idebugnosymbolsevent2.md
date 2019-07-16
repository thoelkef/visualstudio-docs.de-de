---
title: IDebugNoSymbolsEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dadd4547d5b0f691b454a98ba714abea9bf6f058
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323713"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Signalisiert dem [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugger-Benutzeroberfläche auf den Benutzer zu warnen, dass die Symbole für die gestartete ausführbare Datei nicht gefunden.

## <a name="syntax"></a>Syntax

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Von der Debug-Engines implementiert und von der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugger-Benutzeroberfläche.

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
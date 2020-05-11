---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9483c5a434ddfddb3f877111deabea9be6520b05
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726707"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Signalisiert [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] die Debugger-Benutzeroberfläche, um den Benutzer zu warnen, dass Symbole für die gestartete ausführbare Datei nicht gefunden werden konnten.

## <a name="syntax"></a>Syntax

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Wird von Debugmodulen [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementiert und von der Debugger-Benutzeroberfläche verbraucht.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

---
title: IDebugGenericFieldInstance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9723c146ecb5096ea6f3635a3d5cae5c48e573e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728115"
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
Stellt eine Instanz eines Felds für einen generischen Codetyp für verwalteten Code dar.

## <a name="syntax"></a>Syntax

```
IDebugGenericFieldInstance : IUnknown
```

## <a name="methods"></a>Methoden
 Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|Ruft die Typparameterargumente für diese Instanz ab.|
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|Gibt die Anzahl der Typparameterargumente für diese Instanz zurück.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

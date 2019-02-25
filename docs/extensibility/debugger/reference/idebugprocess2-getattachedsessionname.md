---
title: IDebugProcess2::GetAttachedSessionName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa932817c796249803558ad1eb877f620198b3e4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703542"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Ruft den Namen der Sitzung, die diesen Prozess zu Debuggen ist. Eine IDE kann diese Informationen für einen Benutzer anzeigen, die einen bestimmten Prozess auf einem bestimmten Computer Debuggen ist.

> [!NOTE]
>  Diese Methode ist veraltet, und die Implementierung sollte immer zurückgeben `E_NOTIMPL`.

## <a name="syntax"></a>Syntax

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

#### <a name="parameters"></a>Parameter
 `pbstrSessionName`

## <a name="return-value"></a>Rückgabewert
 Diese Methode sollte immer zurückgeben `E_NOTIMPL`.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
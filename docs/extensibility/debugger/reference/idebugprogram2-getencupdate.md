---
title: 'IDebugProgram2:: getencupdate | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e90ff9f8a7a80913aec72b9fe2bb6fe470013d51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722838"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Diese Methode ruft das Update für die Bearbeitung und Fortsetzung (ENC) für dieses Programm ab. Eine benutzerdefinierte Debug-Engine gibt immer `E_NOTIMPL` zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>Parameter
`ppUpdate`\
vorgenommen Gibt eine interne Schnittstelle zurück, die zum Aktualisieren dieses Programms verwendet werden kann.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

> [!NOTE]
> Eine benutzerdefinierte Debug-Engine sollte immer zurückgeben `E_NOTIMPL` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

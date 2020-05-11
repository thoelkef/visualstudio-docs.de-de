---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730046"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Gibt Informationen zurück, die die Erstellung einer vom Menschen lesbaren Fehlermeldung ermöglichen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>Parameter
`pMessageType`\
[out] Gibt einen Wert [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) aus der MESSAGETYPE-Enumeration zurück, der den Nachrichtentyp beschreibt.

`pbstrErrorFormat`\
[out] Das Format der endgültigen Nachricht an den Benutzer (Details finden Sie unter "Anmerkungen").

`hrErrorReason`\
[out] Der Fehlercode, um den es in der Meldung geht.

`pdwType`\
[out] Schweregrad des Fehlers (verwenden Sie `MessageBox`die MB_XXX `MB_EXCLAMATION` `MB_WARNING`Konstanten für ; z. B. oder ).

`pbstrHelpFileName`\
[out] Pfad zu einer Hilfedatei (auf null wert gesetzt, wenn keine Hilfedatei vorhanden ist).

`pdwHelpId`\
[out] ID des anzuzeigenden Hilfethemas (auf 0 gesetzt, wenn kein Hilfethema vorhanden ist).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Fehlermeldung sollte nach . `"What I was doing.  %1"` Der `"%1"` wird dann durch den Aufrufer durch die Fehlermeldung ersetzt, die `hrErrorReason`vom Fehlercode abgeleitet wird (der in zurückgegeben wird). Der `pMessageType` Parameter teilt dem Aufrufer mit, wie die endgültige Fehlermeldung angezeigt werden soll.

## <a name="see-also"></a>Weitere Informationen
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [Messagetype](../../../extensibility/debugger/reference/messagetype.md)

---
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727358"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Diese Schnittstelle wird vom Debugmodul (DE) verwendet, um eine Nachricht an Visual Studio zu senden, die eine Antwort des Benutzers erfordert.

## <a name="syntax"></a>Syntax

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um eine Nachricht an Visual Studio zu senden, die eine Benutzerantwort erfordert. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen.

 Die Implementierung dieser Schnittstelle muss Visual Studios Aufruf von [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) an die DE kommunizieren. Dies kann z. B. mit einer Nachricht erfolgen, die an den Nachrichtenbehandlungsthread der DE gesendet wird, oder das Objekt, das diese Schnittstelle implementiert, kann einen Verweis auf die DE enthalten und mit der an übergebenen Antwort an die DE `IDebugMessageEvent2::SetResponse`zurückrufen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, um eine Nachricht an den Benutzer anzuzeigen, die eine Antwort erfordert. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugMessageEvent2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Ruft die angezeigte Nachricht ab.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Legt die Antwort(en) ggf. aus dem Meldungsfeld fest.|

## <a name="remarks"></a>Bemerkungen
 Die DE verwendet diese Schnittstelle, wenn sie eine bestimmte Antwort des Benutzers für eine bestimmte Nachricht erfordert. Wenn die DE beispielsweise nach dem Versuch, eine Remotenachricht an ein Programm anzuhängen, eine Meldung `IDebugMessageEvent2` "Zugriff verweigert" `MB_RETRYCANCEL`erhält, sendet die DE diese bestimmte Nachricht in einem Ereignis mit dem Nachrichtenfeldstil an Visual Studio. Auf diese Weise kann der Benutzer den Anfügevorgang wiederholen oder abbrechen.

 Die DE gibt an, wie diese Nachricht behandelt werden soll, indem `MessageBox` sie den Konventionen der Win32-Funktion folgt (Details siehe [AfxMessageBox).](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

 Verwenden Sie die [IDebugErrorEvent2-Schnittstelle,](../../../extensibility/debugger/reference/idebugerrorevent2.md) um Nachrichten an Visual Studio zu senden, für die keine Antwort des Benutzers erforderlich ist.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)

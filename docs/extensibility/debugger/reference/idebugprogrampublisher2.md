---
title: IDebugProgramPublisher2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc6f0643066aaca4ba12d9818d449785f6edb752
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011865"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Diese Schnittstelle ermöglicht einem Debugmodul (de) oder benutzerdefinierten Port Zulieferern das Registrieren von Programmen für das Debuggen.

## <a name="syntax"></a>Syntax

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Visual Studio implementiert diese Schnittstelle, um Programme zu registrieren, die gedebuggt werden, damit Sie für das Debuggen über mehrere Prozesse sichtbar sind.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Rufen Sie die com- `CoCreateInstance` Funktion mit `CLSID_ProgramPublisher` auf, um diese Schnittstelle zu erhalten (siehe Beispiel). Ein oder ein benutzerdefinierter Port Lieferant verwendet diese Schnittstelle, um Programmknoten zu registrieren, die Programme darstellen, die gedebuggt werden.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Macht einen Programmknoten für den und den Sitzungs-Debug-Manager (SDM) verfügbar.|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Entfernt einen Programmknoten, sodass er nicht mehr verfügbar ist.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Stellt ein Programm für den und den SDM zur Verfügung.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Entfernt ein Programm, sodass es nicht mehr verfügbar ist.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Legt ein Flag fest, das angibt, dass ein Debugger vorhanden ist.|

## <a name="remarks"></a>Bemerkungen
Diese Schnittstelle macht Programme und Programmknoten verfügbar (d. h., veröffentlicht sie) für die Verwendung durch des und den Sitzungs-Debug-Manager (SDM). Um auf veröffentlichte Programme und Programmknoten zuzugreifen, verwenden Sie die [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) -Schnittstelle. Dies ist die einzige Möglichkeit, wie Visual Studio erkennen kann, dass ein Programm gedeppt wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
In diesem Beispiel wird gezeigt, wie der Programm Verleger instanziiert und ein Programmknoten registriert wird. Dies wird aus dem Tutorial zum [Veröffentlichen des Programm Knotens](/previous-versions/bb161795(v=vs.90))entnommen.

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
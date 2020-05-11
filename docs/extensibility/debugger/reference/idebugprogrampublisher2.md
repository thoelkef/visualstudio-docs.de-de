---
title: IDebugProgramPublisher2 | Microsoft Docs
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
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721524"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Diese Schnittstelle ermöglicht es einem Debugmodul (DE) oder benutzerdefinierten Portlieferanten, Programme für das Debuggen zu registrieren.

## <a name="syntax"></a>Syntax

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Visual Studio implementiert diese Schnittstelle, um zu registrieren, dass Programme gedebuggt werden, um sie für das Debuggen über mehrere Prozesse hinweg sichtbar zu machen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
Rufen Sie `CoCreateInstance` die `CLSID_ProgramPublisher` Funktion von COM auf, um diese Schnittstelle zu erhalten (siehe Beispiel). Ein DE oder ein benutzerdefinierter Portlieferant verwendet diese Schnittstelle, um Programmknoten zu registrieren, die Programme darstellen, die gedebuggt werden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Stellt einen Programmknoten für DEs und den Sitzungsdebug-Manager (SDM) zur Verfügung.|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Entfernt einen Programmknoten, sodass er nicht mehr verfügbar ist.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Stellt ein Programm für DEs und das SDM zur Verfügung.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Entfernt ein Programm, sodass es nicht mehr verfügbar ist.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Legt ein Flag fest, das angibt, dass ein Debugger vorhanden ist.|

## <a name="remarks"></a>Bemerkungen
Diese Schnittstelle stellt Programme und Programmknoten zur Verfügung (d. h. "veröffentlicht" sie) für die Verwendung durch DEs und den Session Debug Manager (SDM). Um auf veröffentlichte Programme und Programmknoten zuzugreifen, verwenden Sie die [IDebugProgramProvider2-Schnittstelle.](../../../extensibility/debugger/reference/idebugprogramprovider2.md) Nur so kann Visual Studio erkennen, dass ein Programm gedebuggt wird.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
In diesem Beispiel wird gezeigt, wie der Programmherausgeber instanziiert und ein Programmknoten registriert wird. Dies wird aus dem [Tutorial, Veröffentlichen des Programmknotens](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae)entnommen.

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

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)

---
title: IDebugProgramPublisher2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f94e7ea830a49db5b95bae3d0d6c50f73e6d3d64
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343138"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Diese Schnittstelle ermöglicht es einer Debug-Engine (DE) oder benutzerdefinierte Portanbieter Programme für das Debuggen zu registrieren.

## <a name="syntax"></a>Syntax

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Visual Studio implementiert diese Schnittstelle zum Registrieren von Programmen, die gedebuggt wird, um sie für das Debuggen durch mehrere Prozesse sichtbar zu machen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Aufrufen von COM `CoCreateInstance` Funktion `CLSID_ProgramPublisher` zum Abrufen dieser Schnittstelle (siehe Beispiel). Ein DE oder einen benutzerdefinierten Port Lieferanten verwendet diese Schnittstelle zum Registrieren von programmknoten, die aktuell gedebuggten Programm darstellen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Stellt ein Programm-Knoten zur Verfügung, und die Sitzung DEs Debug-Manager (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Entfernt einen Knoten für die Anwendung, damit es nicht mehr verfügbar ist.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Stellt ein Programm DEs und das SDM zur Verfügung.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Ein Programm entfernt, sodass sie nicht mehr verfügbar ist.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Legt ein Flag, das angibt, dass ein Debugger vorhanden ist.|

## <a name="remarks"></a>Hinweise
Diese Schnittstelle stellt Programme und programmknoten zur Verfügung (d. h. "veröffentlicht" werden) für die Verwendung von DEs und sitzungsbasierter Debug-Manager (SDM). Verwenden Sie zum Zugriff auf veröffentlichte Programme und programmknoten der [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) Schnittstelle. Dies ist die einzige Möglichkeit, die Visual Studio erkennt, dass ein Programm im Debugmodus befindet.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt den Herausgeber des Programms zu instanziieren, und registrieren einen Programm-Knoten. Diese stammt aus dem Tutorial [Veröffentlichen der Anwendung Knoten](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

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

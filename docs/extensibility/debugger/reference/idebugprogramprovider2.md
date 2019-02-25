---
title: IDebugProgramProvider2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74604e0b3446e33962c6a8e69a69bfc400f0e3e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700171"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Diese registrierten Schnittstelle ermöglicht es der Sitzung Debug Manager (SDM) zum Abrufen von Informationen zu Programmen, die "über veröffentlicht wurden" die [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) Schnittstelle.

## <a name="syntax"></a>Syntax

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Die Debug-Engine (DE) implementiert diese Schnittstelle, um Informationen zu aktuell gedebuggten Programm bereitstellen. Diese Schnittstelle wird im Abschnitt "DE" der Metrik für die Registrierung registriert `metricProgramProvider`, wie in beschrieben [SDK-Hilfsprogramme zum Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Aufrufen von COM `CoCreateInstance` -Funktion mit den `CLSID` des Programm-Anbieters, die aus der Registrierung abgerufen werden. Siehe das Beispiel.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge

|Methode|Beschreibung|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Ruft Informationen über Programme, die ausgeführt wird, in verschiedene Arten gefiltert.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Ruft einen Knoten Programm erhalten eine bestimmte Prozess-ID.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Richtet einen Rückruf an den Anbieterereignisse im Zusammenhang mit bestimmten Arten von Prozessen zu überwachen.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Erstellt ein Gebietsschema für alle sprachspezifische Ressourcen, die von der DE benötigt werden.|

## <a name="remarks"></a>Hinweise
Normalerweise verwendet ein Prozess diese Schnittstelle herausfinden, über die Programme, die in diesem Prozess ausgeführt wird.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [SDK-Hilfsprogramme für das Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

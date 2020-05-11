---
title: IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43557e5d81e5140967a1189e57a350595d0f7220
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721693"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Diese registrierte Schnittstelle ermöglicht es dem Session-Debug-Manager (SDM), Informationen über Programme zu erhalten, die über die [IDebugProgramPublisher2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) "veröffentlicht" wurden.

## <a name="syntax"></a>Syntax

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Das Debugmodul (DE) implementiert diese Schnittstelle, um Informationen zu den zu debuggenden Programmen bereitzustellen. Diese Schnittstelle wird im DE-Abschnitt der `metricProgramProvider`Registrierung mithilfe der Metrik registriert, wie unter [SDK-Hilfsprogramme zum Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)beschrieben.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
Rufen Sie `CoCreateInstance` die Funktion `CLSID` von COM mit der des Programmanbieters auf, die aus der Registrierung abgerufen wird. Siehe Beispiel.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Ruft Informationen über ausgeführte Programme ab, die auf verschiedene Arten gefiltert werden.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Ruft einen Programmknoten ab, der eine bestimmte Prozess-ID erhält.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Erstellt einen Rückruf, um Anbieterereignisse zu überwachen, die bestimmten Arten von Prozessen zugeordnet sind.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Erstellt ein Gebietsschema für alle sprachspezifischen Ressourcen, die von der DE benötigt werden.|

## <a name="remarks"></a>Bemerkungen
Normalerweise verwendet ein Prozess diese Schnittstelle, um mehr über die in diesem Prozess ausgeführten Programme zu erfahren.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

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

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

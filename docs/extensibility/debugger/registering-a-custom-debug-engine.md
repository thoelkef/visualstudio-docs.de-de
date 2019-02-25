---
title: Registrieren einer benutzerdefiniertes Debug-Engine | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb9b7d406e7638a73e9c4db4974d493aa1d38e92
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715322"
---
# <a name="register-a-custom-debug-engine"></a>Registrieren einer benutzerdefinierten Debug-engine
Die Debug-Engine muss registrieren sich selbst als eine Klassenfactory, die folgenden COM-Konventionen als auch mit Visual Studio über den Visual Studio-Registrierungsunterschlüssel zu registrieren.

> [!NOTE]
>  Sie finden ein Beispiel für eine Debug-Engine in diesem Beispiel TextInterpreter registrieren als Teil des basiert die [Lernprogramm: Erstellen einer DebugEngine, die mithilfe von ATL-COM-](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).

## <a name="dll-server-process"></a>DLL-Server-Prozess
 Eine Debug-Engine ist in der Regel in eine eigene DLL als ein COM-Server eingerichtet. Daher muss die Debug-Engine die CLSID des Klassenfactory mit COM registrieren, bevor Visual Studio darauf zugreifen können. Registrieren Sie anschließend die Debug-Engine muss selbst mit Visual Studio, um alle Eigenschaften (als Metriken andernfalls bezeichnet) herstellen die Debug-engine unterstützt. Die Auswahl der Metriken, die in den Visual Studio-Registrierungsunterschlüssel geschrieben, die den Funktionen, die die Debug-Engine unterstützt abhängig ist.

 [SDK-Hilfsprogramme für das debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) beschreibt nicht nur die Registrierungsspeicherorte, die zum Registrieren einer Debug-Engine; Außerdem wird beschrieben, die *dbgmetric.lib* -Bibliothek, die eine Reihe von nützlichen Funktionen und Deklarationen enthält Bearbeiten die Registrierung einfacher für C++-Entwickler, die vornehmen.

### <a name="example"></a>Beispiel
 Das folgende Beispiel (aus dem TextInterpreter-Beispiel) zeigt, wie Sie mit der `SetMetric` Funktion (aus *dbgmetric.lib*), um die Registrierung einer Debug-Engine mit Visual Studio. Die Metriken, die übergeben wird, werden auch definiert *dbgmetric.lib*.

> [!NOTE]
>  TextInterpreter ist es sich um einen einfachen Debug-Engine. Es ist nicht dafür konfiguriert, und registriert daher keine – andere Features. Eine vollständige Debug-Engine müsste eine Liste mit `SetMetric` Aufrufe oder deren äquivalent, eine für jede Funktion die Debug-Engine unterstützt.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Siehe auch
- [Erstellen einer benutzerdefinierten Debug-engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Tutorial: Erstellen einer DebugEngine, die Verwendung von ATL-COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
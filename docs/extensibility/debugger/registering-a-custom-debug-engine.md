---
title: Registrieren einer benutzerdefinierten Debug-Engine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713222"
---
# <a name="register-a-custom-debug-engine"></a>Registrieren eines benutzerdefinierten Debugmoduls
Das Debugmodul muss sich selbst als Klassenfactory registrieren, die COM-Konventionen befolgen, sowie sich über den Visual Studio-Registrierungsunterschlüssel bei Visual Studio registrieren.

> [!NOTE]
> Sie finden ein Beispiel für das Registrieren eines Debugmoduls im TextInterpreter-Beispiel, das als Teil des [Tutorials: Erstellen eines Debugmoduls mit ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)erstellt wurde.

## <a name="dll-server-process"></a>DLL-Serverprozess
 Ein Debugmodul wird in der Regel in einer eigenen DLL als COM-Server eingerichtet. Daher muss das Debugmodul die CLSID seiner Klassenfactory bei COM registrieren, bevor Visual Studio darauf zugreifen kann. Anschließend muss sich das Debugmodul bei Visual Studio registrieren, um alle Eigenschaften (auch als Metriken bezeichnet) einzurichten, die das Debugmodul unterstützt. Die Auswahl der Metriken, die in den Visual Studio-Registrierungsunterschlüssel geschrieben werden, hängt von den Funktionen ab, die das Debugmodul unterstützt.

 [SDK-Hilfsprogramme zum Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) beschreiben nicht nur die Registrierungsspeicherorte, die zum Registrieren eines Debugmoduls erforderlich sind. Außerdem wird die *Dbgmetric.lib-Bibliothek* beschrieben, die eine Reihe nützlicher Funktionen und Deklarationen für C++-Entwickler enthält, die das Bearbeiten der Registrierung erleichtern.

### <a name="example"></a>Beispiel
 Das folgende Beispiel (aus dem TextInterpreter-Beispiel) zeigt, wie sie die `SetMetric` Funktion (von *dbgmetric.lib*) verwendet, um ein Debugmodul bei Visual Studio zu registrieren. Die übergebenen Metriken werden auch in *dbgmetric.lib*definiert.

> [!NOTE]
> TextInterpreter ist ein grundlegendes Debugmodul; Es werden keine anderen Features eingerichtet – und daher nicht registriert. Ein vollständigeres Debugmodul hätte `SetMetric` eine ganze Liste von Aufrufen oder deren Äquivalent, eine für jedes Feature, das das Debugmodul unterstützt.

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

## <a name="see-also"></a>Weitere Informationen
- [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [SDK-Hilfsprogramme zum Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Tutorial: Erstellen eines Debugmoduls mit ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

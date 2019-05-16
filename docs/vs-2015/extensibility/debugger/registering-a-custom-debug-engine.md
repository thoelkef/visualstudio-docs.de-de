---
title: Registrieren einer benutzerdefiniertes Debug-Engine | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703601"
---
# <a name="registering-a-custom-debug-engine"></a>Registrieren einer benutzerdefinierten Debug-Engine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Debug-Engine muss registrieren sich selbst als eine Klassenfactory, gemäß COM-Konventionen als auch mit Visual Studio über den Visual Studio-Registrierungsunterschlüssel zu registrieren.  
  
> [!NOTE]
> Ein Beispiel zum Registrieren einer Debug-Engine finden Sie im Beispiel TextInterpreter, das als Teil des integriert ist die [Lernprogramm: Erstellen einer DebugEngine, die mithilfe von ATL-COM-](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>DLL-Server-Prozess  
 In der Regel ist eine Debug-Engine in eine eigene DLL als ein COM-Server implementiert. Dies bedeutet, dass die Debug-Engine die CLSID des Klassenfactory mit COM registrieren muss, bevor Visual Studio darauf zugreifen können. Die Debug-Engine selbst mit Visual Studio selbst registrieren muss gewahrt Eigenschaften (als Metriken andernfalls bezeichnet) die Debug-engine unterstützt. Die Auswahl der Metriken, die für die Debug-Engine im Visual Studio-Registrierungsunterschlüssel geschrieben werden, hängt von der Features, die die Debug-Engine unterstützt.  
  
 [SDK-Hilfsprogramme zum Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) beschreibt nicht nur die Registrierungsspeicherorte, die zum Registrieren einer Debug-Engine; Außerdem wird beschrieben, die dbgmetric.lib-Bibliothek, die enthält eine Reihe von nützlichen Funktionen und-Deklarationen für C++-Entwickler, die machen Bearbeiten der Registrierungs vereinfacht.  
  
### <a name="example"></a>Beispiel  
 Folgendes ist ein typisches Beispiel (aus dem TextInterpreter-Beispiel), die zur Verwendung der `SetMetric` funktionieren (von dbgmetric.lib), um eine Debug-Engine mit Visual Studio zu registrieren. Die Metriken, die übergeben wird, werden auch in dbgmetric.lib definiert.  
  
> [!NOTE]
> TextInterpreter ist es sich um einen einfachen Debug-Engine. wird nicht implementiert, und daher nicht registriert, andere Features. Eine vollständige Debug-Engine müsste eine Liste mit `SetMetric` Aufrufe oder deren äquivalent, eine für jede Funktion die Debug-Engine unterstützt.  
  
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
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Erstellen einer DebugEngine, die Verwendung von ATL-COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)

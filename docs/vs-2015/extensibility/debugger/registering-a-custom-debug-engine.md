---
title: Registrieren einer benutzerdefinierten Debug-Engine | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703601"
---
# <a name="registering-a-custom-debug-engine"></a>Registrieren einer benutzerdefinierten Debug-Engine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Debug-Engine muss sich als Klassenfactory gemäß com-Konventionen registrieren und mit Visual Studio über den Registrierungs Unterschlüssel von Visual Studio registrieren.  
  
> [!NOTE]
> Ein Beispiel für die Registrierung einer Debug-Engine finden Sie im Textinterpreter-Beispiel, das im Rahmen des [Tutorials: Erstellen einer Debug-Engine mithilfe von ATL-COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)erstellt wird.  
  
## <a name="dll-server-process"></a>DLL-Server Prozess  
 In der Regel wird eine Debug-Engine in ihrer eigenen dll als com-Server implementiert. Dies bedeutet, dass die Debug-Engine die CLSID ihrer Klassenfactory bei com registrieren muss, bevor Visual Studio darauf zugreifen kann. Dann muss sich die Debug-Engine selbst bei Visual Studio registrieren, um Eigenschaften (auch als Metriken bezeichnet) zu erstellen, die von der Debug-Engine unterstützt werden. Die Auswahl der Metriken, die in den Visual Studio-Registrierungs Unterschlüssel für die Debug-Engine geschrieben werden, hängt von den Funktionen ab, die die Debug-Engine unterstützt  
  
 [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) beschreiben nicht nur die Registrierungs Speicherorte, die zum Registrieren einer Debug-Engine erforderlich Außerdem wird die Bibliothek "dbgmetric. lib" beschrieben, die eine Reihe nützlicher Funktionen und Deklarationen für C++-Entwickler enthält, die die Bearbeitung der Registrierung vereinfachen.  
  
### <a name="example"></a>Beispiel  
 Im folgenden finden Sie ein typisches Beispiel (aus dem Textinterpreter-Beispiel), das zeigt `SetMetric` , wie Sie die-Funktion (aus dbgmetric. lib) zum Registrieren einer Debug-Engine bei Visual Studio verwenden. Die zu über gebenden Metriken werden auch in dbgmetric. lib definiert.  
  
> [!NOTE]
> Textinterpreter ist eine einfache Debug-Engine. Er implementiert – nicht und registriert – keine anderen Features. Eine vollständigere Debug-Engine verfügt über eine vollständige Liste mit `SetMetric` aufrufen oder deren Entsprechung, eine für jedes Feature, das die Debug-Engine unterstützt.  
  
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
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [SDK-Hilfsprogramme zum Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: aufbauen einer Debug-Engine mithilfe von ATL-COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)

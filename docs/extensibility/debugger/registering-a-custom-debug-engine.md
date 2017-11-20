---
title: Registrieren ein benutzerdefiniertes Modul Debuggen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58f58a1a6ec80331fd5cf6f735098c16c35db82e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="registering-a-custom-debug-engine"></a>Registrieren einer benutzerdefinierten Debugmodul
Debugging-Modul muss registriert sich selbst als Klassenfactory gemäß COM-Konventionen sowie mit Visual Studio über den Visual Studio-Registrierungsunterschlüssel registrieren.  
  
> [!NOTE]
>  Ein Beispiel zum Registrieren von Debugging-Modul finden Sie in der Stichprobe TextInterpreter, die im Rahmen des basiert die [Lernprogramm: erstellen eine Debug-Modul mithilfe von ATL-COM-](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>DLL-Server-Prozess  
 In der Regel wird ein Debugging-Modul in eine eigene DLL als com-Server implementiert. Dies bedeutet, dass die Debugging-Modul die CLSID des Klassenfactory mit COM registrieren muss, bevor Visual Studio darauf zugreifen können. Und Debugging-Modul selbst mit Visual Studio selbst registrieren muss gewahrt Eigenschaften (als Metriken andernfalls bezeichnet) der Debug-engine unterstützt. Die Auswahl von Metriken, die in der Visual Studio-Registrierungsunterschlüssel für das Debugging-Modul geschrieben werden, hängt von den Funktionen ab, die Debugging-Modul unterstützt, ab.  
  
 [SDK-Hilfsprogramme zum Debugging](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) beschreibt nicht nur Speicherorte in der Registrierung registriert ein Debugmodul; Außerdem wird erläutert, die dbgmetric.lib-Bibliothek, die enthält eine Reihe von nützlichen Funktionen und Deklarationen für C++-Entwickler, die Stellen Bearbeiten der Registrierungs, die einfacher zu können.  
  
### <a name="example"></a>Beispiel  
 Folgender Ausdruck ist ein typisches Beispiel (aus dem TextInterpreter-Beispiel) zur Verwendung der `SetMetric` -Funktion (von dbgmetric.lib), um ein Debugmodul mit Visual Studio zu registrieren. Die Metriken, die übergeben werden, werden auch in dbgmetric.lib definiert.  
  
> [!NOTE]
>  TextInterpreter ist eine grundlegende Debugmodul. nicht implementiert, und daher nicht registriert – beliebige andere Funktionen. Eine umfassendere Debugmodul müsste eine vollständige Liste der `SetMetric` Aufrufe oder das Äquivalent eines für jede Funktion die Debugging-Modul unterstützt.  
  
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
 [Erstellen einer benutzerdefinierten Debugmodul](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Lernprogramm: Erstellen einer Debugging-Modul unter Verwendung von ATL-COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)
---
title: "Registrieren einer benutzerdefinierten Debugmodul | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, registrieren"
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrieren einer benutzerdefinierten Debugmodul
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Debugging\-Modul muss selbst eine Klassenfactory, die folgenden COM\-Konventionen registrieren, als auch mit Visual Studio über die Visual Studio\-Registrierungsunterschlüssel registrieren.  
  
> [!NOTE]
>  Ein Beispiel für ein Debugmodul registrieren finden Sie im Beispiel TextInterpreter wird als Teil des basiert die [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/de-de/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## DLL\-Server\-Prozess  
 In der Regel wird ein Debugging\-Modul in eine eigene DLL als com\-Server implementiert. Dies bedeutet, dass das Debugging\-Modul die CLSID der Klasse ab Werk mit COM registrieren muss, bevor Visual Studio darauf zugreifen können. Und dann das Debugmodul selbst mit Visual Studio selbst registrieren muss gewahrt werden Eigenschaften \(als Metriken andernfalls bezeichnet\) das Debuggen engine unterstützt. Die Auswahl der Metriken, die in der Visual Studio\-Registrierungsunterschlüssel für das Debugging\-Modul geschrieben werden, hängt von Funktionen, die das Debugging\-Modul unterstützt.  
  
 [SDK\-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Beschreibt die nicht nur Speicherorte in der Registrierung erforderlich, dass ein Debugging\-Modul. Es beschreibt auch die Bibliothek dbgmetric.lib enthält eine Reihe von nützlichen Funktionen und Deklarationen für C\+\+\-Entwickler, die Bearbeitung der Registrierungs einfacher machen.  
  
### Beispiel  
 Im folgenden finden Sie z. B. \(aus dem Beispiel TextInterpreter\) zur Verwendung der `SetMetric` \-Funktion \(von dbgmetric.lib\), um ein Debugmodul mit Visual Studio zu registrieren. Die Metriken übergeben wird, werden auch in dbgmetric.lib definiert.  
  
> [!NOTE]
>  TextInterpreter ist eine grundlegende Debugging\-Modul. wird nicht implementiert, und werden daher nicht registriert, andere Features. Ein vollständiges Debugmodul müsste eine ganze Liste `SetMetric` aufrufen oder die entsprechenden, eine für jede Funktion die Debugging\-Modul unterstützt.  
  
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
  
## Siehe auch  
 [Erstellen einer benutzerdefinierten Debugmodul](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [SDK\-Hilfsprogramme für das Debuggen](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/de-de/9097b71e-1fe7-48f7-bc00-009e25940c24)
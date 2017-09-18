---
title: "IDebugProgramProvider2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2"
helpviewer_keywords: 
  - "IDebugProgramProvider2-Schnittstelle"
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgramProvider2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese registrierte Schnittstelle ermöglicht der Sitzung Debuggen von Manager \(SDM\) zum Abrufen von Informationen zu Programmen, die von der [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) „Schnittstelle“ veröffentlicht worden sind.  
  
## Syntax  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um Informationen über die Anwendungen bereitzustellen, die gedebuggt werden.  Diese Schnittstelle wird in DE section mithilfe der Registrierung registriert `metricProgramProvider`metrischen, wie in [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)beschrieben.  
  
## Hinweise für Aufrufer  
 `CoCreateInstance`\-Funktion des Aufrufs COM mit `CLSID` des Programms Anbieters, der aus der Registrierung abgerufen wird.  Weitere Informationen finden Sie im Beispiel.  
  
## Methoden in die Vtable\-Reihenfolge  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Ruft Informationen über die ausgeführte Programme, die gefiltert in einer Vielzahl von Methoden.|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Ruft den Knoten ab, wenn ein Programm eine bestimmte Prozessnummer|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Richtet einen Rückruf für Anbieter ein, um Ereignisse zu überwachen, die mit bestimmten Arten von Prozessen zugeordnet sind.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Richtet das Gebietsschema für alle sprachspezifischen Ressourcen, die vom DE benötigt werden.|  
  
## Hinweise  
 Normalerweise verwendet ein Prozess über diese Schnittstelle, um Programme zu ermitteln, die in diesem Prozess ausgeführt werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Beispiel  
  
```cpp#  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
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
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [SDK\-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
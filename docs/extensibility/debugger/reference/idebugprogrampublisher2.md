---
title: "IDebugProgramPublisher2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2"
helpviewer_keywords: 
  - "IDebugProgramPublisher2-Schnittstelle"
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramPublisher2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht eine Debug\- Modul \(DE\) oder benutzerdefinierte Anschlusslieferanten zu registrierende programmen für das Debuggen.  
  
## Syntax  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um Programme zu registrieren, die gedebuggt werden, dass sie sichtbar zu machen zum Debuggen über mehre Prozesse hinweg erhalten bleiben.  
  
## Hinweise für Aufrufer  
 `CoCreateInstance`\-Funktion des Aufrufs COM mit `CLSID_ProgramPublisher` , zum Abrufen dieser Schnittstelle \(siehe Beispiel\).  DE lieferant oder einen benutzerdefinierten Port verwendet diese Schnittstelle, um Knoten Programm zu registrieren, die die Programme darstellen, die gedebuggt werden.  
  
## Methoden in die Vtable\-Reihenfolge  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Legt einen Knoten Programm für den Debug\- und den Manager der Sitzung \(SDM\).|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Entfernt einen Knoten Programm, sodass er nicht mehr verfügbar ist.|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Legt ein Programm DES und SDM zur Verfügung.|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Entfernt ein Programm. Daher ist es nicht mehr verfügbar.|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Legt ein Flag fest, das angibt, dass ein Debugger vorhanden ist.|  
  
## Hinweise  
 Diese Schnittstelle macht Programme und Programmierung verfügbaren Knoten \(d. h. „veröffentlicht sie“\), die für den Debug\- und den Manager der Sitzung \(SDM\).  Um veröffentlichte Programm Programme und Knoten zuzugreifen, verwenden Sie die [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)\-Schnittstelle.  Dies ist die einzige Möglichkeit, die Visual Studio erkennen kann, dass ein Programm gedebuggt wird.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Beispiel  
 Dieses Beispiel zeigt, wie Sie den Herausgeber des Programms und instanziiert einen Knoten Programm registriert.  Dies wird vom Lernprogramm, [Publishing the Program Node](http://msdn.microsoft.com/de-de/d0100e02-4e2b-4e72-9e90-f7bc11777bae)übernommen.  
  
```cpp#  
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
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
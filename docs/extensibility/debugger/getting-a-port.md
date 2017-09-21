---
title: "Abrufen eines Ports | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Abrufen von Ports"
  - "Debuggen [Debugging-SDK]-ports"
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Abrufen eines Ports
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Port stellt eine Verbindung mit einem Computer dar, auf dem Prozesse ausgeführt werden.  Dieser Computer konnte auf dem lokalen Computer oder einem Remotecomputer befinden \(die möglicherweise ein nicht\-WINDOWS\-basiertes Betriebssystem ausgeführt werden kann. Weitere Informationen finden Sie unter [Ports](../../extensibility/debugger/ports.md) \).  
  
 Ein Port wird von der [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)\-Schnittstelle dargestellt.  Er wird verwendet, um Informationen über die Prozesse zu erhalten, die auf dem Computer ausgeführt werden, den der Anschluss verbunden ist.  
  
 Ein Debuggen Modul benötigt Zugriff auf einen Anschluss, um Knoten mit dem Programm Anschluss registrieren und verarbeitet Informationen zu Anforderungen zu erfüllen.  Wenn z. B. das Debugmodul die [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md)\-Schnittstelle implementiert, kann die Implementierung für die [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)\-Methode den Port um die erforderlichen Informationen zum Prozess angefordert zurückgegeben werden soll.  
  
 Visual Studio\-Zubehör der notwendige Anschluss an das Modul und Debuggen von einem Port dieser den Anschlusslieferanten.  Wenn ein Programm angefügt wurde \(entweder aus dem Debugger oder aufgrund einer Ausnahme wurde ausgelöst, die das die Dialogfeld \[Just\-In\-Time\]\) gestartet wird, kann der Benutzer die Auswahl zu verwendende angegebene des Transports \(ein anderer Name für den Anschlusslieferanten\).  Wenn der Benutzer das Programm im Debugger gestartet wird, gibt das Projektsystem den Anschlusslieferanten an, der verwendet werden soll.  In jedem Ereignis instanziiert Visual Studio den Anschlusslieferanten, dargestellt durch eine [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)\-Schnittstelle und fordert einen neuen Anschluss, indem [Port hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) mit einer [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)\-Schnittstelle aufruft.  Dieser Port wird dann an den ein Modul in der Debug\- oder anderen Form übergeben.  
  
## Beispiel  
 Dieses Codefragment zeigt, wie Sie den Port, der zu [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) angegeben wird, um einen Knoten in [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)Programm zu registrieren.  Die Parameter nicht direkt mit diesem Konzept wird aus Gründen der Übersichtlichkeit weggelassen.  
  
> [!NOTE]
>  Dieses Beispiel verwendet den Port, um den Vorgang fortzusetzen und den Prozess zu starten und setzt voraus, dass die [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)\-Schnittstelle im Anschluss implementiert wird.  Dies ist auf keinen Fall die einzige Möglichkeit, diese Aufgaben auszuführen, und es besteht die Möglichkeit, dass der Port auch nicht möglicherweise anders beteiligt ist, [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) des Programms verfügen, das zuvor angegeben ist.  
  
```cpp#  
// This is an IDebugEngineLaunch2 method.  
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                      IDebugPort2 *pPort,  
                                      /* omitted parameters */,  
                                      IDebugProcess2**ppDebugProcess)  
{  
    // do stuff here to set up for a launch (such as handling the other parameters)  
    ...  
  
    // Now get the IPortNotify2 interface so we can register a program node  
    // in CDebugEngine::ResumeProcess.  
    CComPtr<IDebugDefaultPort2> spDefaultPort;  
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
    if (SUCCEEDED(hr))  
    {  
        CComPtr<IDebugPortNotify2> spPortNotify;  
        hr = spDefaultPort->GetPortNotify(&spPortNotify);  
        if (SUCCEEDED(hr))  
        {  
            // Remember the port notify so we can use it in ResumeProcess.  
            m_spPortNotify = spPortNotify;  
  
            // Now launch the process in a suspended state and return the  
            // IDebugProcess2 interface  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = pPort->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                // pass on the parameters we were given (omitted here)  
                hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
            }  
        }  
    }  
    return(hr);  
}  
  
HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
{  
    // Make a program node for this process  
    HRESULT hr;  
    CComPtr<IDebugProgramNode2> spProgramNode;  
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
    if (SUCCEEDED(hr))  
    {  
        hr = m_spPortNotify->AddProgramNode(spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            // resume execution of the process using the port given to us earlier.  
           // (Querying for the IDebugPortEx2 interface is valid here since  
           // that's how we got the IDebugPortNotify2 interface in the first place.)  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = m_spPortNotify->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## Siehe auch  
 [Registrieren die Anwendung](../../extensibility/debugger/registering-the-program.md)   
 [Ein Programm zum Debuggen aktivieren](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Port\-Lieferanten](../../extensibility/debugger/port-suppliers.md)   
 [Ports](../../extensibility/debugger/ports.md)
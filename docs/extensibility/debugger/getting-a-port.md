---
title: Abrufen eines Ports | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5f6065c91845df020325e279a1fa3858a4f75505
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="getting-a-port"></a>Abrufen eines Ports
Ein Port stellt eine Verbindung mit einem Computer, auf dem Prozesse ausgeführt werden. Dieser Computer ist möglicherweise der lokale Computer oder einem Remotecomputer (dem konnte möglicherweise ein nicht-Windows-basierten Betriebssystem ausführen, finden Sie unter [Ports](../../extensibility/debugger/ports.md) für Weitere Informationen).  
  
 Ein Port wird dargestellt, durch die [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) Schnittstelle. Es dient zum Abrufen von Informationen über Prozesse, die auf dem Computer, dem der Port verbunden ist.  
  
 Ein Debugmodul benötigt Zugriff auf einen Port aus, um Programm Knoten mit dem Port zu registrieren und die Anforderungen für Prozessinformationen erfüllen. Angenommen, die Debugging-Modul implementiert die [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) schnittstellenimplementierung, die für die [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) Methode Fragen den Port für den Prozess erforderlich die Informationen zurückgegeben werden sollen.  
  
 Visual Studio stellt die erforderlichen Ports an die Debugging-Modul, und sie diesen Port von einem anderen Port Lieferanten abruft. Wenn ein Programm angefügt ist (innerhalb des Debuggers oder aufgrund einer Ausnahme wurde ausgelöst, die im Dialogfeld Just-in-Time [JIT] löst), der Benutzer erhält die Auswahl des Transports (einen anderen Namen für einen Port Lieferanten) verwenden. Wenn der Benutzer die Anwendung von innerhalb des Debuggers gestartet wird, gibt das Projektsystem, andernfalls Lieferanten Port verwenden. Visual Studio instanziiert in jedem Fall den Port-Lieferanten, dargestellt durch eine [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) Schnittstelle, und fordert einen neuen Port durch Aufrufen von [hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) mit einer [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) Schnittstelle. Dieser Port wird dann an die Debugging-Modul in einem Formular oder eine andere übergeben.  
  
## <a name="example"></a>Beispiel  
 Dieses Codefragment zeigt, wie den Port für angegebene [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) Registrieren eines Knotens Programm in [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parameter, die nicht direkt auf dieses Konzept beziehen, wurden aus Gründen der Übersichtlichkeit ausgelassen.  
  
> [!NOTE]
>  In diesem Beispiel verwendet den Port starten und den Vorgang fortsetzen und setzt voraus, dass die [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) Schnittstelle wird implementiert, an dem Port. Dies ist nicht die einzige Möglichkeit zum Ausführen dieser Aufgaben aus, und es ist möglich, dass der Port nicht selbst außer beteiligt sein kann, müssen des Programms [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) angegeben.  
  
```cpp  
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
  
## <a name="see-also"></a>Siehe auch  
 [Registrieren das Programm](../../extensibility/debugger/registering-the-program.md)   
 [Aktivieren ein Programm, das gedebuggt werden](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Port-Lieferanten](../../extensibility/debugger/port-suppliers.md)   
 [Ports](../../extensibility/debugger/ports.md)
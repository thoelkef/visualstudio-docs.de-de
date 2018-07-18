---
title: Registrieren das Programm | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: febc798888cc046e514db4013edb077e25f5aaca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126300"
---
# <a name="registering-the-program"></a>Registrieren das Programm
Nachdem die Debugging-Modul einen Port abgerufen wurden, dargestellt durch eine [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) Schnittstelle im nächsten Schritt aktivieren das Programm, das gedebuggt werden mit dem Port registriert ist. Nach der Registrierung kann das Programm debuggen, indem Sie eine der folgenden Methoden:  
  
-   Der Prozess der anfügen, der dem Debugger ermöglicht, eine ausgeführte Anwendung debuggen vollständige Kontrolle zu erhalten.  
  
-   Just-in-Time (JIT) Debuggen, wodurch für nach der Tatsache Debuggen eines Programms, die unabhängig von einem Debugger ausgeführt wird. Wenn die Architektur zur Laufzeit einen Fehler abgefangen, der Debugger wird benachrichtigt, bevor Sie das Betriebssystem oder Laufzeitumgebung frei, den Arbeitsspeicher und die Ressourcen des Programms einen Fehler auslösenden.  
  
## <a name="registering-procedure"></a>Registrieren der Prozedur  
  
#### <a name="to-register-your-program"></a>Um das Programm zu registrieren.  
  
1.  Rufen Sie die [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) Methode, die vom Port implementiert.  
  
     `IDebugPortNotify2::AddProgramNode` erfordert einen Zeiger auf eine [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle.  
  
     Wenn das Betriebssystem oder die Laufzeitumgebung einer Anwendung geladen wird, erstellt es in der Regel die Programm-Knoten. Wenn die Debugging-Modul (DE) aufgefordert, laden das Programm anschließend DE erstellt und registriert die Programm-Knoten.  
  
     Das folgende Beispiel zeigt die Debugging-Modul, das Programm, und registrieren es mit einem Port.  
  
    > [!NOTE]
    >  Dies ist nicht die einzige Möglichkeit zum Starten und Fortsetzen eines Prozesses. Dies ist vor allem ein Beispiel für ein Programm mit einem Port registrieren.  
  
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
 [Abrufen eines Ports](../../extensibility/debugger/getting-a-port.md)   
 [Aktivieren eines Programms für das Debuggen](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
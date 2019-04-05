---
title: Registrieren des Programms | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc4a8de9f93a04fb062954703a1c14b4c4447308
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958128"
---
# <a name="registering-the-program"></a>Registrieren des Programms
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nachdem die Debug-Engine einen Port erworben hat, dargestellt durch ein [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle, im nächsten Schritt aktivieren das Programm debuggt werden wird, um ihn mit dem Port zu registrieren. Nach der Registrierung kann das Programm debuggen, indem Sie eine der folgenden Methoden:  
  
-   Der Prozess anfügen, der mit dem Debugger ermöglicht, die vollständige debugging Kontrolle einer ausgeführten Anwendung zu erhalten.  
  
-   Just-in-Time (JIT) Debuggen, was nach der dem Ereignis Debuggen eines Programms, das unabhängig von einem Debugger ausgeführt wird. Wenn die Architektur für die Laufzeit einen Fehler abfängt, wird der Debugger vor dem Betriebssystem benachrichtigt oder Laufzeitumgebung frei, die Arbeitsspeicher- und Ressourcen des fehlerhaften Programms.  
  
## <a name="registering-procedure"></a>Registrieren die Prozedur  
  
#### <a name="to-register-your-program"></a>Registrieren Sie Ihr Programm  
  
1.  Rufen Sie die [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) Methode, die vom Port implementiert.  
  
     `IDebugPortNotify2::AddProgramNode` erfordert einen Zeiger auf ein [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle.  
  
     Wenn das Betriebssystem oder die Laufzeitumgebung ein Programm geladen wird, erstellt es in der Regel die Programm-Knoten. Wenn die Debug-Engine (DE) aufgefordert wird, um die Anwendung zu laden. Klicken Sie dann die DE erstellt, und den Programm-Knoten registriert.  
  
     Das folgende Beispiel zeigt die Debug-Engine, das Programm gestartet und mit einem Port zu registrieren.  
  
    > [!NOTE]
    >  Dies ist nicht die einzige Möglichkeit zum Starten und Fortsetzen eines Prozesses. Dies ist vor allem ein Beispiel für ein Programm mit einem Port zu registrieren.  
  
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
                    hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)  
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

---
title: "Registrieren die Anwendung | Microsoft Docs"
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
  - "Programme, die Registrierung"
  - "Registrierung Programm Debuggen [SDK-Debuggen]"
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrieren die Anwendung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nachdem das Debugmodul einen Port abgerufen hat, dargestellt durch eine [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)\-Schnittstelle, der nächste Schritt darin, während das Programm gedebuggt werden soll, sie mit dem Port zu registrieren.  Sobald registriert, ist das Programm für das Debuggen durch Folgendes bedeutet:  
  
-   Beim Anfügen, der den Debugger an den vollständigen Debuggings die Steuerung des Gewinnes eine ausgeführte Anwendung kann.  
  
-   Rechtzeitiges Debuggen \(Just\-In\-Time\), das Nach\-d Tatsache Debuggen eines Programms zulässt, das unabhängig von einem Debugger ausgeführt wird.  Wenn die Architektur der Laufzeit einen Fehler abfängt, wird der Debugger vor dem Betriebssystem oder Momentaufnahme für die Versionen der Laufzeit Arbeitsspeicher und die Ressourcen des bemängelnden Programm benachrichtigt.  
  
## Registrieren der Prozedur  
  
#### So führen Sie das Programm registrieren  
  
1.  Nennen Sie die [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)\-Methode implementiert durch den Anschluss.  
  
     `IDebugPortNotify2::AddProgramNode` erfordert einen Zeiger auf eine [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)\-Schnittstelle.  
  
     Normalerweise wenn das Betriebssystem oder die Laufzeitumgebung ein Programm lädt, erstellt er den Knoten Programm.  Wenn das Debugmodul \(DE\) aufgefordert wird, das Programm zu laden, DE erstellt und registriert den Knoten Programm.  
  
     Das folgende Beispiel zeigt das Debugmodul, das das Programm gestartet wird und durch ein Anschluss registriert.  
  
    > [!NOTE]
    >  Dies ist nicht die einzige Möglichkeit zu öffnen und einen Vorgang fortsetzen. Dies ist vor allem ein Beispiel für das Registrierens eines Programms mit einem Port.  
  
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
 [Abrufen eines Ports](../../extensibility/debugger/getting-a-port.md)   
 [Ein Programm zum Debuggen aktivieren](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
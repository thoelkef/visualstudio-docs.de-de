---
title: Registrieren des Programms | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b68fa67f784d155288482ad724b632ed5ba5fa41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713171"
---
# <a name="register-the-program"></a>Registrieren des Programms
Nachdem das Debugmodul einen Port erworben hat, der durch eine [IDebugPort2-Schnittstelle](../../extensibility/debugger/reference/idebugport2.md) dargestellt wird, besteht der nächste Schritt, um das zu debuggende Programm zu ermöglichen, darin, ihn beim Port zu registrieren. Nach der Registrierung steht das Programm für das Debuggen auf eine der folgenden Arten zur Verfügung:

- Der Prozess des Anfügens, der es dem Debugger ermöglicht, die vollständige Debugsteuerung einer ausgeführten Anwendung zu erhalten.

- Just-in-Time (JIT)-Debugging, das das nachdemmalige Debuggen eines Programms ermöglicht, das unabhängig von einem Debugger ausgeführt wird. Wenn die Laufzeitarchitektur einen Fehler abfängt, wird der Debugger benachrichtigt, bevor das Betriebssystem oder die Laufzeitumgebung den Speicher und die Ressourcen des fehlerhaften Programms freigibt.

## <a name="registering-procedure"></a>Registrierungsverfahren

### <a name="to-register-your-program"></a>So registrieren Sie Ihr Programm

1. Rufen Sie die [AddProgramNode-Methode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) auf, die vom Port implementiert wurde.

     `IDebugPortNotify2::AddProgramNode`erfordert einen Zeiger auf eine [IDebugProgramNode2-Schnittstelle.](../../extensibility/debugger/reference/idebugprogramnode2.md)

     Wenn das Betriebssystem oder die Laufzeitumgebung ein Programm lädt, wird normalerweise der Programmknoten erstellt. Wenn das Debugmodul (DE) aufgefordert wird, das Programm zu laden, erstellt und registriert die DE den Programmknoten.

     Das folgende Beispiel zeigt, wie das Debugmodul das Programm startet und bei einem Port registriert.

    > [!NOTE]
    > Dieses Codebeispiel ist nicht die einzige Möglichkeit, einen Prozess zu starten und fortzusetzen. Dieser Code ist hauptsächlich ein Beispiel für die Registrierung eines Programms bei einem Port.

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

## <a name="see-also"></a>Weitere Informationen
- [Abrufen eines Ports](../../extensibility/debugger/getting-a-port.md)
- [Debuggen eines Programms](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

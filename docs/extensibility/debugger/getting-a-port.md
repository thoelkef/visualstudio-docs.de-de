---
title: Erhalten eines Ports | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738632"
---
# <a name="get-a-port"></a>Holen Sie sich einen Port
Ein Port stellt eine Verbindung zu einem Computer dar, auf dem Prozesse ausgeführt werden. Bei diesem Computer kann es sich um den lokalen Computer oder einen Remotecomputer (der möglicherweise ein nicht Windows-basiertes Betriebssystem ausführen könnte) sein. Weitere Informationen finden Sie unter [Ports).](../../extensibility/debugger/ports.md)

Ein Port wird durch die [IDebugPort2-Schnittstelle](../../extensibility/debugger/reference/idebugport2.md) dargestellt. Es wird verwendet, um Informationen über Prozesse zu erhalten, die auf dem Computer ausgeführt werden, mit dem der Port verbunden ist.

Ein Debugmodul benötigt Zugriff auf einen Port, um Programmknoten beim Port zu registrieren und Anforderungen für Prozessinformationen zu erfüllen. Wenn das Debugmodul beispielsweise die [IDebugProgramProvider2-Schnittstelle](../../extensibility/debugger/reference/idebugprogramprovider2.md) implementiert, kann die Implementierung für die [GetProviderProcessData-Methode](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) den Port auffordern, die erforderlichen Prozessinformationen zurückzugeben.

Visual Studio stellt den erforderlichen Port für das Debugmodul bereit, und es ruft diesen Port von einem Portlieferanten ab. Wenn ein Programm angefügt ist (entweder innerhalb des Debuggers oder aufgrund einer Ausnahme, die das Just-in-Time [JIT]-Dialogfeld auslöst), erhält der Benutzer die Wahl des Transports (ein anderer Name für einen Portlieferanten), der verwendet werden soll. Andernfalls gibt das Projektsystem den zu verwendenden Portlieferanten an, wenn der Benutzer das Programm innerhalb des Debuggers startet. In beiden Instanziierungen instanziiert Visual Studio den Portanbieter, der durch eine [IDebugPortSupplier2-Schnittstelle](../../extensibility/debugger/reference/idebugportsupplier2.md) dargestellt wird, und fragt nach einem neuen Port, indem [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) mit einer [IDebugPortRequest2-Schnittstelle](../../extensibility/debugger/reference/idebugportrequest2.md) aufgerufen wird. Dieser Port wird dann in der einen oder anderen Form an das Debugmodul übergeben.

## <a name="example"></a>Beispiel
Dieses Codefragment zeigt, wie Sie den Port verwenden, der [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) zum Registrieren eines Programmknotens in [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)bereitgestellt wird. Parameter, die nicht direkt mit diesem Konzept zusammenhängen, wurden aus Gründen der Übersichtlichkeit weggelassen.

> [!NOTE]
> In diesem Beispiel wird der Port zum Starten und Fortsetzen des Prozesses verwendet und davon ausgegangen, dass die [IDebugPortEx2-Schnittstelle](../../extensibility/debugger/reference/idebugportex2.md) auf dem Port implementiert ist. Dies ist bei weitem nicht die einzige Möglichkeit, diese Aufgaben auszuführen, und es ist möglich, dass der Port nicht einmal beteiligt ist, außer dass der [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) des Programms ihm gegeben wird.

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
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>Weitere Informationen
- [Registrieren des Programms](../../extensibility/debugger/registering-the-program.md)
- [Debuggen eines Programms](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Hafenlieferanten](../../extensibility/debugger/port-suppliers.md)
- [Ports](../../extensibility/debugger/ports.md)

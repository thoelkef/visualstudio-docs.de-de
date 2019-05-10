---
title: Abrufen eines Ports | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25b703eafccb412c33640a9e73e72afa09c0c277
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889891"
---
# <a name="get-a-port"></a>Abrufen eines Ports
Ein Port stellt eine Verbindung mit einem Computer, die für den Prozesse ausgeführt werden. Kann es sich bei diesen Computer dem lokalen Computer oder einem Remotecomputer (die konnte möglicherweise ein nicht-Windows-basierten Betriebssystem ausführen, finden Sie unter [Ports](../../extensibility/debugger/ports.md) Informationen).

Ein Port wird dargestellt, durch die [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) Schnittstelle. Es wird zum Abrufen von Informationen zu Prozessen, die auf dem Computer, dem der Port verbunden ist.

Eine Debug-Engine benötigt Zugriff auf einen Port aus, um das Registrieren von programmknoten mit dem Port und für Prozessinformationen eingehenden Anforderungen zu erfüllen. Z. B., wenn die Debug-Engine implementiert die [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) schnittstellenimplementierung, die für die [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) Methode den Port für den Prozess der erforderlichen Fragen Informationen, die zurückgegeben werden soll.

Visual Studio stellt den erforderlichen Port an, die Debug-Engine, und sie diesen Port von eines portanbieters abruft. Wenn ein Programm angefügt ist (entweder innerhalb des Debuggers oder aufgrund einer Ausnahme wurde ausgelöst, die löst des Dialogfeld für die Just-in-Time [JIT]), der Benutzer erhält die Auswahl des Transports (ein anderer Name für eine Anschlusslieferanten) verwenden. Wenn der Benutzer die Anwendung von innerhalb des Debuggers startet, gibt das Projektsystem, andernfalls Anschlusslieferanten verwenden. Visual Studio instanziiert in jedem Fall Anschlusslieferanten, dargestellt durch ein [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle und durch Aufrufen von aufgefordert, einen neuen Port [Port hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) mit einer [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) Schnittstelle. Dieser Port wird dann an die Debug-Engine in einem Formular oder eine andere übergeben.

## <a name="example"></a>Beispiel
Dieses Codefragment zeigt, wie Sie den Port für angegebene verwenden [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) registrieren Sie einen Programm-Knoten in [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parameter, die nicht in direktem Zusammenhang mit diesem Konzept wurden aus Gründen der Übersichtlichkeit ausgelassen.

> [!NOTE]
> In diesem Beispiel verwendet den Port starten und Fortsetzen des Vorgangs, und setzt voraus, dass die [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) Schnittstelle wird implementiert, auf dem Port. Dies ist keineswegs die einzige Möglichkeit zum Ausführen dieser Aufgaben aus, und es ist möglich, dass der Port nicht selbst außer beteiligt sein kann damit der Anwendung die [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) an es übergeben.

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

## <a name="see-also"></a>Siehe auch
- [Registrieren des Programms](../../extensibility/debugger/registering-the-program.md)
- [Aktivieren eines Programms, die debuggt werden](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Portanbieter](../../extensibility/debugger/port-suppliers.md)
- [Ports](../../extensibility/debugger/ports.md)

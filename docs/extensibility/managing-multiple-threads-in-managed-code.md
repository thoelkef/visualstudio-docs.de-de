---
title: 'Vorgehensweise: Verwalten von mehreren Threads in verwaltetem Code | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1173b55a3e22d7a2fec9ecdb0440765beb970e6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693099"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Vorgehensweise: Verwalten von mehreren Threads in verwaltetem code
Wenn Sie eine verwaltete VSPackage-Erweiterung, die asynchrone Methoden aufrufen oder Vorgänge, die auf anderen Threads als dem Visual Studio-UI-Thread ausgeführt wurde verfügen, sollten Sie die folgenden Richtlinien befolgen. Sie können den UI-Thread reaktionsfähig halten, da muss nicht warten, Arbeit auf einem anderen Thread abgeschlossen. Sie können Ihren Code effizienter, vornehmen, da Sie nicht über zusätzliche Threads verfügen, die Stapelspeicherplatz einnehmen, und können Sie es machen, zuverlässiger und einfacher zu debuggen, da Sie, Deadlocks und Blockaden vermeiden.

 Sie können im Allgemeinen vom UI-Thread wechseln, zu einem anderen Thread aus, oder umgekehrt. Bei der Rückgabe der Methode ist der aktuelle Thread der Thread, von dem es ursprünglich aufgerufen wurde.

> [!IMPORTANT]
>  Die folgenden Richtlinien verwenden Sie die APIs in der <xref:Microsoft.VisualStudio.Threading> Namespace, insbesondere die <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> Klasse. Die APIs in diesem Namespace sind neu in [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Erhalten Sie eine Instanz von einem <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> aus der <xref:Microsoft.VisualStudio.Shell.ThreadHelper> Eigenschaft `ThreadHelper.JoinableTaskFactory`.

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Wechseln Sie vom im UI-Thread in einem Hintergrundthread

1.  Wenn Sie auf der UI-Thread und asynchronen arbeiten in einem Hintergrundthread verwenden möchten `Task.Run()`:

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2.  Wenn Sie die UI-Thread und synchron blockiert, während Sie arbeiten in einem Hintergrundthread, Verwendung durchführen möchten die <xref:System.Threading.Tasks.TaskScheduler> Eigenschaft `TaskScheduler.Default` in <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Wechseln Sie von einem Hintergrundthread zum UI-thread

1.  Wenn Sie in einem Hintergrundthread und etwas der UI-Thread verwendet werden sollen <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Sie können die <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Methode, um zum UI-Thread zu wechseln. Diese Methode sendet eine Meldung an den UI-Thread mit der Fortsetzung der aktuellen asynchronen Methode, und zudem kommuniziert er mit dem Rest von threading Framework legen Sie die richtige Priorität und Deadlocks zu vermeiden.

     Wenn die Hintergrund-Thread-Methode nicht asynchron ist und Sie können nicht sie asynchrone, können Sie dennoch verwenden die `await` Syntax, um zum UI-Thread zu wechseln, indem Sie die Arbeit mit wrapping <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, wie in diesem Beispiel:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
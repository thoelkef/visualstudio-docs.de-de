---
title: 'Gewusst wie: Verwalten mehrerer Threads in verwaltetem Code | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702782"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Gewusst wie: Verwalten mehrerer Threads in verwaltetem Code
Wenn Sie über eine verwaltete VSPackage-Erweiterung verfügen, die asynchrone Methoden aufruft oder Vorgänge hat, die auf anderen Threads als dem Visual Studio-UI-Thread ausgeführt werden, sollten Sie die nachstehenden Richtlinien befolgen. Sie können den UI-Thread reaktionsfähig halten, da er nicht warten muss, bis die Arbeit an einem anderen Thread abgeschlossen ist. Sie können Den Code effizienter gestalten, da Sie keine zusätzlichen Threads haben, die Stapelspeicher belegen, und Sie können ihn zuverlässiger und einfacher debuggen lassen, da Sie Deadlocks und Hängen vermeiden.

 Im Allgemeinen können Sie vom UI-Thread zu einem anderen Thread wechseln oder umgekehrt. Wenn die Methode zurückgegeben wird, ist der aktuelle Thread der Thread, von dem er ursprünglich aufgerufen wurde.

> [!IMPORTANT]
> Die folgenden Richtlinien verwenden die <xref:Microsoft.VisualStudio.Threading> APIs im Namespace, insbesondere in der <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> Klasse. Die APIs in diesem Namespace sind neu in [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Sie können eine Instanz <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> von <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory`a von der Eigenschaft abrufen.

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Wechseln vom UI-Thread zu einem Hintergrundthread

1. Wenn Sie sich im UI-Thread befinden und asynchrone Arbeiten `Task.Run()`an einem Hintergrundthread erledigen möchten, verwenden Sie:

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Wenn Sie sich im UI-Thread befinden und synchron blockieren möchten, während Sie <xref:System.Threading.Tasks.TaskScheduler> `TaskScheduler.Default` arbeiten <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>an einem Hintergrundthread arbeiten, verwenden Sie die Eigenschaft in:

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Wechseln von einem Hintergrundthread zum UI-Thread

1. Wenn Sie sich in einem Hintergrundthread befinden und etwas im <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>UI-Thread tun möchten, verwenden Sie:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Sie können <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> die Methode verwenden, um zum UI-Thread zu wechseln. Diese Methode sendet eine Nachricht an den UI-Thread mit der Fortsetzung der aktuellen asynchronen Methode und kommuniziert auch mit dem Rest des Threadingframeworks, um die richtige Priorität festzulegen und Deadlocks zu vermeiden.

     Wenn die Hintergrundthreadmethode nicht asynchron ist und Sie sie nicht asynchron machen `await` können, können Sie die Syntax dennoch <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>verwenden, um zum UI-Thread zu wechseln, indem Sie Ihre Arbeit mit umschließen, wie in diesem Beispiel:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```

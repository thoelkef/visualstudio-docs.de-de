---
title: Wechseln zu einem anderen Thread während des Debuggens
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31eb3427a441b4b79bbd57d9da9871118173b15c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60051282"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Vorgehensweise: Wechseln zu einem anderen Thread während des Debuggens in Visual Studio (C#, Visual Basic C++)
Beim Debuggen einer Multithreadanwendung können Sie eine von mehreren Methoden verwenden, um über den Thread zu wechseln, die Sie zu einem anderen Thread gearbeitet haben.

> [!NOTE]
> Wenn Sie die Reihenfolge steuern, in denen Threads ausführen, möchten, müssen Sie [Einfrieren und Reaktivieren von Threads](../debugger/get-started-debugging-multithreaded-apps.md).

Wenn Sie Threads im Code-Editor und die verschiedenen Multithread-debugging-Fenster die überprüfen, gibt der gelbe Pfeil des aktuellen Threads an. Ein grüner Pfeil in Form einer Welle gibt an, dass eine nicht-aktuellen Threads den aktuellen Debuggerkontext hat.

### <a name="to-switch-to-any-thread-that-appears"></a>Wechseln Sie an einen beliebigen Thread, der angezeigt wird

- In der **Threads** oder **parallele Überwachung** Fenster, doppelklicken Sie auf den Thread.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>So wechseln Sie zu einem Thread in einem Quellcodefenster

- Im linken Bundsteg, mit der Maustaste ein Thread-Marker-Symbol ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker"), zeigen Sie auf **wechseln Sie zur**, und klicken Sie dann auf den Namen des Threads, zu dem Sie wechseln möchten, . Im Kontextmenü werden nur die Threads an dieser bestimmten Position angezeigt.

     Wenn kein Threadmarker angezeigt werden, mit der Maustaste in den **Threads** Fenster, und überprüfen Sie, ob **Threads in Quelle anzeigen** ausgewählt ist.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>So wechseln Sie über die Symbolleiste Debugspeicherort zu einem Thread

1. Auf der **Debugspeicherort** -Symbolleiste klicken Sie auf die **Thread** Liste.

2. Klicken Sie in der Liste auf den Thread, zu dem Sie wechseln möchten.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)

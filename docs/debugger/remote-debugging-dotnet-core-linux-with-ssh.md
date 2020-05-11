---
title: Remote Debuggen von .net Core unter Linux | Microsoft-Dokumentation
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23bc0fa990a79b1855ec382f42248a0f847c3c9c
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/29/2020
ms.locfileid: "78200866"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>Remote Debuggen von .net Core unter Linux mithilfe von SSH

Ab Visual Studio 2017 können Sie .net Core-Prozesse, die unter Linux ausgeführt werden, über SSH anfügen. In diesem Artikel wird beschrieben, wie Sie das Debuggen einrichten und Debuggen.

## <a name="prerequisites"></a>Voraussetzungen

Auf dem Visual Studio-Computer müssen Sie entweder die Arbeitsauslastung **ASP.net und Webentwicklung** oder die Platt **Form übergreifende .net Core-Entwicklung** installieren.

Auf dem Linux-Server müssen Sie den SSH-Server installieren, entpacken und mit curl oder wget installieren. Beispielsweise können Sie dies unter Ubuntu ausführen, indem Sie Folgendes ausführen:

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>Erstellen und Bereitstellen der Anwendung

So bereiten Sie die Anwendung für das Debuggen vor:

- Verwenden Sie beim Erstellen der Anwendung ggf. eine Debugkonfiguration. Das Debuggen von im Einzelhandel kompilierten Code (eine Releasekonfiguration) als debugkompilierter Code ist weitaus schwieriger. Wenn Sie eine Releasekonfiguration verwenden müssen, deaktivieren Sie zuerst nur eigenen Code. Um diese Einstellung zu deaktivieren, **Wählen Sie** Extras > **Optionen** > **Debugging**aus, und deaktivieren Sie dann **nur eigenen Code aktivieren**.

- Stellen Sie sicher, dass Ihr Projekt für die Erstellung [portabler pdsb](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (Standardeinstellung) konfiguriert ist, und stellen Sie sicher, dass sich die pbds am gleichen Speicherort wie die DLL befinden. Um dies in Visual Studio zu konfigurieren, klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie dann **Eigenschaften** >  > **Erweiterte** > **Debuginformationen** **Erstellen** aus.

Sie können mehrere Methoden verwenden, um die APP vor dem Debuggen bereitzustellen. Beispielsweise können Sie folgende Aktionen ausführen:

- Kopieren Sie die Quellen auf den Zielcomputer, und erstellen Sie mit ```dotnet build``` auf dem Linux-Computer.

- Erstellen Sie die APP unter Windows, und übertragen Sie die buildartefakte auf den Linux-Computer. (Die buildartefakte bestehen aus der Anwendung selbst, allen Laufzeitbibliotheken, von denen Sie abhängig sein kann, und der *deps. JSON* -Datei.)

## <a name="attach-the-debugger"></a>Anfügen des Debuggers

Nachdem die Computer konfiguriert sind, starten Sie die Anwendung auf dem Linux-Computer. Anschließend können Sie den Debugger anfügen.

1. Wählen Sie in Visual Studio die Option **Debuggen** > **an den Prozess anhängen...** .

1. Wählen Sie in der Liste **Verbindungstyp** die Option **SSH**aus.

1. Ändern Sie das **Verbindungs Ziel** in die IP-Adresse oder den Hostnamen des Ziel Computers.

1. Suchen Sie den Prozess, den Sie debuggen möchten.

   Der Code wird entweder in einem eindeutigen Prozessnamen oder einem Prozess mit dem Namen "dotnet" ausgeführt. Um den gewünschten Prozess zu finden, überprüfen Sie die Spalte **Title** , in der die Befehlszeilenargumente für den Prozess angezeigt werden.

   Im folgenden Beispiel sehen Sie eine Liste der Prozesse von einem Linux-Remote Computer über einen SSH-Transport, der im Dialogfeld **an den Prozess anhängen** angezeigt wird.

   ![An Linux-Prozess anfügen](media/remote-debug-linux-over-ssh-attach.png)

1. Wählen Sie **Anfügen**aus.

1. Wählen Sie im angezeigten Dialogfeld den Codetyp aus, den Sie debuggen möchten. Wählen Sie **verwaltet (.net Core für UNIX) aus**.

1. Debuggen Sie die App mithilfe von Visual Studio-Debugfunktionen.

   Im folgenden Beispiel wird der Visual Studio-Debugger an einem Haltepunkt im Code angehalten, der auf einem Linux-Remote Computer ausgeführt wird.

   ![Treffen eines Haltepunkts](media/remote-debug-linux-over-ssh-hit-breakpoint.png)
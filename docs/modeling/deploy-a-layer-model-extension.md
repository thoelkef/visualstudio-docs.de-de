---
title: Bereitstellen einer Ebenenmodellerweiterung
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8fe915f31181af4158bdfe7e292313886ed7d4c
ms.sourcegitcommit: 4c7a0c2d712eb24609216577a793e912a6083eaf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "57983103"
---
# <a name="deploy-a-layer-model-extension"></a>Bereitstellen einer Ebenenmodellerweiterung

Andere Benutzer von Visual Studio können Ebenenmodellierungserweiterungen installieren, die Sie mithilfe von Visual Studio erstellt haben.

## <a name="install-your-extension"></a>Installieren der Erweiterungs

Die Erweiterung wird zu einer VSIX-Datei kompiliert, die Sie auf anderen Computern installieren können. Sie können sie auch auf dem Entwicklungscomputer installieren, um die Erweiterung in der Hauptinstanz von Visual Studio verfügbar zu machen.

### <a name="to-install-the-extension"></a>So installieren Sie die Erweiterung

1. Klicken Sie in das Projekt mit **source.vsix.manifest**öffnen die *Bin* Verzeichnis, in dem Datei-Explorer.

2. Kopieren der  **\*VSIX** Datei auf dem Computer, auf denen die Erweiterung installiert werden sollen.

3. Doppelklicken Sie auf dem Zielcomputer auf die VSIX-Datei in Windows-Explorer.

    Das VSIX-Installationsprogramm wird geöffnet.

### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung

::: moniker range="vs-2017"

1. Wählen Sie in Visual Studio **Tools** > **Erweiterungen und Updates**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie in Visual Studio **Erweiterungen** > **Verwalten von Erweiterungen**.

::: moniker-end

2. Klicken Sie auf den Namen der Erweiterung, und klicken Sie dann auf **Deinstallieren**.

## <a name="install-an-extension-on-team-foundation-server"></a>Installieren Sie eine Erweiterung für Team Foundation Server

Team Foundation Server-Servern müssen normalerweise keine Visual Studio installiert, und Sie können nicht so die VSIX-Datei installieren, indem Sie darauf doppelklicken. Sie müssen die Erweiterung manuell installieren.

### <a name="to-install-your-layer-extension-on-a-team-foundation-server-server"></a>So installieren Sie die ebenenerweiterung auf einem Server für Team Foundation Server

1.  Kopieren der. *Vsix* Dateien vom Entwicklungscomputer auf den Team Foundation Server (TFS)-Computer.

     Speichern Sie die VSIX-Datei in einem der folgenden Speicherorte:

    -   So führen Sie die Installation für alle Benutzer und Dienste aus:

         %ProgramFiles%\Microsoft Visual Studio [Version]\Common7\IDE\Extensions\Microsoft

    -   So installieren Sie nur für den Netzwerkdienst, der den Build ausgeführt wird:

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   Wenn Sie den Build zur Ausführung im interaktiven Modus als einen bestimmten Benutzer konfiguriert haben, können Sie nur für diesen Benutzer installieren:

         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

2.  Erweitern Sie jede VSIX-Datei in einen Ordner am gleichen Speicherort:

    1.  Ändern Sie die Dateierweiterung von **VSIX** zu **ZIP**.

    2.  Extrahieren Sie den Inhalt der ZIP-Datei in einen Ordner.

    3.  Löschen Sie die ZIP-Datei.

3.  Starten Sie TFS neu.

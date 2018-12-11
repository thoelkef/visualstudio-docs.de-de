---
title: Installieren einer Vorschauversion
description: Anleitung zum Aktualisieren von Visual Studio für Mac und Zugreifen auf Vorschauversionen, einschließlich der Vorschauversionen von Visual Studio 2019 für Mac
zone_pivot_groups: mac-ide-version
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 0E1EF257-9DE4-4653-9DF4-805CE007A1A1
ms.openlocfilehash: b5eea8c2c894b7eeaa13c83ae6698d1297de9297
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896756"
---
# <a name="install-a-preview-release"></a>Installieren einer Vorschauversion

::: zone pivot="vsmac2019"

> [!TIP]
> Die Vorschauversion von Visual Studio 2019 für Mac ist jetzt verfügbar. Zum ersten Mal kann die Vorschauversion parallel mit dem aktuellen stabilen Release von Visual Studio für Mac installiert werden.

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Anforderungen für die Vorschauversion von Visual Studio 2019 für Mac

* Ein Mac mit macOS High Sierra 10.13 oder höher.

Darüber hinaus benötigen Sie zum Erstellen von Xamarin-Apps für iOS oder macOS:

* Xcode 10.0 oder höher. Für gewöhnlich wird die neuste stabile Version empfohlen.
* eine Apple-ID Erstellen Sie eine kostenlose Apple-ID unter https://appleid.apple.com, wenn Sie noch keine besitzen. Dies ist für die Installation von und die Anmeldung bei Xcode erforderlich.

## <a name="installing-the-preview"></a>Installieren der Vorschauversion

1. Laden Sie das Installationsprogramm für die Vorschauversion von der [Seite „Visual Studio für Mac (Vorschau)“](https://aka.ms/vs4mac-preview) herunter.
2. Klicken Sie nach Abschluss des Downloads auf **VisualStudioforMacPreviewInstaller.dmg**, um den Installer einzubinden. Führen Sie ihn anschließend durch Doppelklicken auf das Pfeillogo aus:

    [![Auf großen Pfeil klicken, um die Installation zu starten](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. Möglicherweise wird Ihnen eine Warnmeldung angezeigt, in der Sie darauf hingewiesen werden, dass die Anwendung aus dem Internet heruntergeladen wird. Klicken Sie auf **Öffnen**.
4. Warten Sie, während das Installationsprogramm Ihr System überprüft:

    [![Das Installationsprogramm überprüft Ihr System auf installierte Komponenten](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. Ihnen wird eine Warnmeldung angezeigt, in der Sie dazu aufgefordert werden, die Datenschutz- und Lizenzbedingungen zu akzeptieren. Klicken Sie zum Lesen der Bedingungen auf die Links, und klicken Sie auf **Weiter**, wenn Sie die Bedingungen akzeptieren:

    [![Klicken Sie auf die Links zu den Datenschutz- und Lizenzbedingungen, und fahren Sie fort, wenn Sie diese akzeptieren](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. Die Liste der verfügbaren Workloads wird angezeigt. Wählen Sie die Workloads aus, die Sie verwenden möchten:

    [![Wählen Sie aus, welche optionalen Workload-Features Sie gerne installieren würden](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    Wenn Ihre aktuelle Version von Visual Studio 2017 für Mac älter als Version 7.7 ist, werden Sie dazu aufgefordert, ein Upgrade auf die aktuelle stabile Version zu genehmigen (dieses Upgrade unterstützt die parallele Installation). Klicken Sie auf **Weiter**, um das Upgrade zu genehmigen:

    ![Die Durchführung eines Upgrades für die stabile Version auf 7.7 ist erforderlich](media/install-preview-older-upgrade.png)

7. Klicken Sie auf die Schaltfläche **Installieren**, nachdem Sie Ihre Auswahl getroffen haben.
8. Das Installationsprogramm zeigt während des Downloads den Fortschritt an und installiert Visual Studio für Mac sowie die ausgewählten Workloads. Möglicherweise werden Sie dazu aufgefordert, Ihr Kennwort einzugeben, um die für die Installation erforderlichen Berechtigungen zu erteilen.
9. Sie können **Visual Studio (Vorschauversion)** jederzeit verwenden, wenn Sie die Vorschauversion testen möchten, oder für Ihre Produktionsarbeit wieder zur aktuellen stabilen Version von Visual Studio wechseln. Hier werden die beiden Symbole angezeigt:

    ![Unterschiede zwischen den Symbolen für die stabile Version und die Vorschauversion](media/install-preview-icons-sml.png)

Wenn während der Installation in einer Unternehmensumgebung Netzwerkprobleme auftreten, lesen Sie die Anweisungen unter [Installation hinter einer Firewall oder einem Proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Informationen zu den Änderungen in den [Versionshinweisen](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

::: zone-end
::: zone pivot="vsmac2017"

## <a name="install-an-update-for-visual-studio-2017-for-mac"></a>Installieren eines Updates für Visual Studio 2017 für Mac

Vor der offiziellen Freigabe einer neuen Version von Visual Studio für Mac ist diese als Vorschauversion verfügbar. Die Vorschauversion bietet Ihnen die Möglichkeit, neue Features zu testen und die neuesten Fehlerkorrekturen zu erhalten, bevor diese vollständig in das Produkt integriert werden.

Vorschauversionen zu Visual Studio für Mac werden als Update und nicht über einen separaten Download verteilt. Wie im [Aktualisieren](update.md)-Artikel beschrieben, verfügt Visual Studio für Mac über drei Updatekanäle: Stabil, Beta und Alpha.

Die meisten Vorschauversionen sind über die beiden Kanäle **Beta** und **Alpha** verfügbar, prüfen Sie aber stets die [Anmerkungen zur Vorschauversion](/visualstudio/releasenotes/vs2017-mac-preview-relnotes), um möglichst genaue Informationen zu erhalten.

Um die Vorschauversion von Visual Studio für Mac zu installieren, verwenden Sie die folgenden Schritte:

1. Wechseln Sie zu **Visual Studio > Nach Updates suchen**.
2. Wählen Sie im Kombinationsfeld „Update channel“ (Updatekanal) die Option **Beta** aus.
3. Wählen Sie die Schaltfläche **Switch channel** (Kanal wechseln) aus, um zum ausgewählten Kanal zu wechseln und mit dem Herunterladen etwaiger neuer Updates zu beginnen.
4. Um die Installation der Updates zu starten, wählen Sie die Schaltfläche **Neu starten und Updates installieren** aus.

Weitere Informationen zum Aktualisieren in Visual Studio für Mac finden Sie im [Aktualisieren](update.md)-Artikel.

::: zone-end
---
title: Deinstallieren von Visual Studio
titleSuffix: ''
description: Erfahren Sie Schritt für Schritt, wie Sie Visual Studio deinstallieren.
ms.date: 05/06/2020
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9d1412d6e015ec7d05e700370c7a379ada9a57b0
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419093"
---
# <a name="uninstall-visual-studio"></a>Deinstallieren von Visual Studio

Diese Seite führt Sie durch die Deinstallation von Visual Studio, unserer integrierten Suite von Produktivitätstools für Entwickler.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Deinstallieren von Visual Studio für Mac](/visualstudio/mac/uninstall).

> [!TIP]
> Wenn Sie Probleme mit Ihrer Instanz von Visual Studio haben, verwenden Sie das **Reparaturtool**. Weitere Informationen finden Sie unter [Reparieren von Visual Studio](../install/repair-visual-studio.md). 
>
> Wenn Sie den Speicherort für einige Ihrer Visual Studio-Dateien ändern möchten, ist dies möglich, ohne die aktuelle Instanz zu deinstallieren. Weitere Informationen finden Sie unter [Auswählen der Installationspfade in Visual Studio](../install/change-installation-locations.md).
>
> Allgemeine Tipps zur Problembehandlung finden Sie unter [Problembehandlung der Visual Studio-Installation und von Upgradefehlern](../install/troubleshooting-installation-issues.md).

::: moniker range="vs-2017"

1. Suchen Sie den Visual Studio-Installer auf Ihrem Computer.

     Auf einem Computer mit Windows 10 Anniversary Update oder höher klicken Sie beispielsweise auf **Start** und scrollen zum Buchstaben **V**. Dort wird das Installationsprogramm als **Visual Studio-Installer** angezeigt.

     ![Visual Studio-Installer](media/locate-the-visual-studio-installer.png "Suchen des Microsoft Visual Studio-Installers")

   > [!NOTE]
   > Auf manchen Computern ist der Visual Studio-Installer unter dem Buchstaben **„M“** als **Microsoft Visual Studio-Installer** aufgelistet.<br/><br/> Alternativ dazu finden Sie den Visual Studio-Installer in folgendem Speicherort: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Suchen Sie im Installer nach der Edition von Visual Studio, die Sie installiert haben. Als Nächstes wählen Sie **Mehr** und dann **Deinstallieren** aus.

     ![Deinstallieren von Visual Studio 2017](media/uninstall-visual-studio.png "Deinstallieren von Visual Studio 2017")

1. Klicken Sie zur Bestätigung Ihrer Auswahl auf **OK**.

Wenn Sie Ihre Meinung später ändern und Visual Studio 2017 erneut installieren möchten, starten Sie den Visual Studio-Installer erneut, und wählen Sie dann auf dem Auswahlbildschirm **Installieren** aus.

## <a name="uninstall-visual-studio-installer"></a>Deinstallieren des Visual Studio-Installers

Um alle Installationen von Visual Studio 2017 und den Visual Studio-Installer vollständig von Ihrem Computer zu entfernen, deinstallieren Sie es unter „Apps & Funktionen“.

1. Unter Windows 10 geben Sie im Feld „Geben Sie hier Text für die Suche ein.“ den Begriff **Apps und Features** ein.
1. Suchen Sie nach **Microsoft Visual Studio 2017** (oder **Visual Studio 2017**).
1. Klicken Sie auf **Deinstallieren**.
1. Suchen Sie dann den **Microsoft Visual Studio-Installer**.
1. Klicken Sie auf **Deinstallieren**.

::: moniker-end

::: moniker range="vs-2019"

1. Suchen Sie den Visual Studio-Installer auf Ihrem Computer.

     Auf einem Computer mit Windows 10 wählen Sie beispielsweise **Start** und blättern dann zum Buchstaben **V**, wo das Installationsprogramm als **Visual Studio-Installer** angezeigt wird.

     ![Öffnen des Visual Studio-Installers](media/vs-2019/vs-installer-windows-start.png "Öffnen des Visual Studio-Installers")

     > [!NOTE]
     > Sie können den Visual Studio-Installer auch an folgendem Speicherort finden:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Möglicherweise müssen Sie den Installer aktualisieren, bevor Sie fortfahren. Wenn dies der Fall ist, befolgen Sie die Anweisungen.

1. Suchen Sie im Installer nach der Edition von Visual Studio, die Sie installiert haben. Als Nächstes wählen Sie **Mehr** und dann **Deinstallieren** aus.

     ![Deinstallieren von Visual Studio 2019](media/vs-2019/vs-installer-uninstall.png "Deinstallieren von Visual Studio 2019")

1. Klicken Sie zur Bestätigung Ihrer Auswahl auf **OK**.

     ![Bestätigung der Deinstallation von Visual Studio](media/vs-2019/uninstall-visualstudio-confirm.png "Bestätigen, dass Sie Visual Studio 2019 deinstallieren möchten")

Falls Sie Visual Studio 2019 später doch wieder installieren möchten, starten Sie den Visual Studio-Installer erneut, wählen Sie die Registerkarte **Available** (Verfügbar) aus, wählen Sie die Visual Studio-Edition aus, die Sie installieren möchten, und klicken Sie dann auf **Installieren**.

## <a name="uninstall-visual-studio-installer"></a>Deinstallieren des Visual Studio-Installers

Um alle Installationen von Visual Studio 2019 und den Visual Studio-Installer von Ihrem Computer zu entfernen, deinstallieren Sie es unter „Apps & Funktionen“.

1. Unter Windows 10 geben Sie im Feld „Geben Sie hier Text für die Suche ein.“ den Begriff **Apps und Features** ein.
1. Suchen Sie **Visual Studio 2019**.
1. Klicken Sie auf **Deinstallieren**.
1. Suchen Sie dann den **Microsoft Visual Studio-Installer**.
1. Klicken Sie auf **Deinstallieren**.

::: moniker-end

## <a name="remove-all-files"></a>Entfernen aller Dateien

Wenn ein schwerwiegender Fehler auftritt und Visual Studio nicht mithilfe der vorherigen Anweisungen deinstalliert werden kann, gibt es eine Option für einen „letzten Ausweg“, die Sie stattdessen verwenden können. Weitere Informationen zum vollständigen Entfernen aller Visual Studio-Installationsdateien und Produktinformationen finden Sie auf der Seite [Entfernen von Visual Studio](remove-visual-studio.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Ändern von Visual Studio](modify-visual-studio.md)
* [Visual Studio aktualisieren](update-visual-studio.md)

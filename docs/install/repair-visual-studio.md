---
title: Reparieren Sie Visual Studio.
titleSuffix: ''
description: Hier erfahren Sie, wie Sie eine Installation von Visual Studio 2017 reparieren.
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 255995f7ca660d36ae40a6a8fead4b3ea5d70424
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594551"
---
# <a name="repair-visual-studio"></a>Reparieren Sie Visual Studio.

::: moniker range="vs-2017"

Es kann vorkommen, dass Ihre Visual Studio-Installation beschädigt wird oder fehlerhaft ist. Dies kann durch eine Reparatur behoben werden.

1. Suchen Sie den **Visual Studio-Installer** auf Ihrem Computer.

     Auf einem Computer mit Windows 10 Anniversary Update oder höher klicken Sie beispielsweise auf **Start** und scrollen dann zum Buchstaben **V**. Dort wird das Installationsprogramm als **Visual Studio-Installer** angezeigt.

   > [!NOTE]
   > Auf manchen Computern ist der Visual Studio-Installer unter dem Buchstaben **„M“** als **Microsoft Visual Studio-Installer** aufgelistet.
   >
   > Alternativ dazu finden Sie den Visual Studio-Installer in folgendem Speicherort: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Öffnen Sie den Installer, wählen Sie **Mehr** aus, und wählen Sie dann **Reparieren** aus.

    ![Reparieren von Visual Studio über den Visual Studio-Installer](media/repair-visual-studio.png "Reparieren von Visual Studio über den Visual Studio-Installer")

   > [!NOTE]
   > Durch das Reparieren von Visual Studio wird die Umgebung zurückgesetzt. Lokale Anpassungen wie Erweiterungen pro Benutzer, die ohne erweiterte Berechtigungen installiert wurden, Benutzereinstellungen und Profile werden entfernt. Ihre synchronisierten Einstellungen wie Designs, Farben und Tastenzuordnungen werden wiederhergestellt.
   >

   > [!TIP]
   > Die Option **Reparieren** wird nur für installierte Instanzen von Visual Studio angezeigt. Ist die Option **Reparieren** nicht vorhanden, haben Sie möglicherweise **Mehr** für eine Version ausgewählt, die im Visual Studio-Installer als "Verfügbar" und nicht als "Installiert" aufgeführt ist.

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

1. Suchen Sie im Installer nach der Edition von Visual Studio, die Sie installiert haben. Als Nächstes wählen Sie **Mehr** aus, und wählen Sie dann **Reparieren** aus.

     ![Reparieren von Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Reparieren von Visual Studio 2019")

   > [!NOTE]
   > Durch das Reparieren von Visual Studio wird die Umgebung zurückgesetzt. Lokale Anpassungen wie Erweiterungen pro Benutzer, die ohne erweiterte Berechtigungen installiert wurden, Benutzereinstellungen und Profile werden entfernt. Ihre synchronisierten Einstellungen wie Designs, Farben und Tastenzuordnungen werden wiederhergestellt.
   >

   > [!TIP]
   > Die Option **Reparieren** wird nur für installierte Instanzen von Visual Studio angezeigt. Ist die Option **Reparieren** nicht vorhanden, haben Sie möglicherweise **Mehr** für eine Version ausgewählt, die im Visual Studio-Installer als "Verfügbar" und nicht als "Installiert" aufgeführt ist.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Visual Studio aktualisieren](update-visual-studio.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)
* [Problembehandlung bei der Visual Studio-Installation und bei Upgradefehlern](troubleshooting-installation-issues.md)

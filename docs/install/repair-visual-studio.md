---
title: Reparieren Sie Visual Studio.
titleSuffix: ''
description: Hier erfahren Sie, wie Sie eine Installation von Visual Studio 2017 reparieren.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3ba5cdf7ba627bc1d6a75368d90da5ce8a726a5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973212"
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

     ![Öffnen des Visual Studio-Installers](media/vs2019-visual-studio-installer.png "Öffnen des Visual Studio-Installers")

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

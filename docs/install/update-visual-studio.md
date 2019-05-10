---
title: Aktualisieren von Visual Studio 2017
titleSuffix: ''
description: Erfahren Sie, wie Sie Visual Studio auf das neueste Release aktualisieren.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a64256f44e9de5bbfd9e65dd6410b9911aaf5075
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997799"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Aktualisieren von Visual Studio auf die neueste Version

::: moniker range="vs-2017"

Sie sollten auf die [aktuelle Version](/visualstudio/releasenotes/vs2017-relnotes/) von Visual Studio 2017 aktualisieren, damit Sie immer die neuesten Features, Fehlerbehebungen und Verbesserungen erhalten.

Wenn Sie die nächste Version ausprobieren möchten, können Sie auch den [Release Candidate](//visualstudio/releases/2019/release-notes/) von Visual Studio 2019 herunterladen.

> [!IMPORTANT]
> Zum Installieren, Aktualisieren und Anpassen von Visual Studio müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt. Weitere Informationen finden Sie unter [Benutzerberechtigungen und Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Aktualisieren von Visual Studio für Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Aktualisieren auf Visual Studio 2017 Version 15.6 oder höher

Wir haben die Durchführung von Installation und Update optimiert, um Ihnen die direkte Verwendung aus IDE heraus zu erleichtern. Hier wird das Aktualisieren von Version 15.6 und später auf neuere Versionen von Visual Studio erklärt.

### <a name="using-the-notifications-hub"></a>Verwenden des Benachrichtigungshubs

Wenn ein Update vorhanden ist, wird ein entsprechendes Benachrichtigungsflag in Visual Studio angezeigt.

1. Speichern Sie Ihre Arbeit.

1. Klicken Sie auf das Benachrichtigungsflag, um den **Benachrichtigungshub** zu öffnen, und wählen Sie dann das Update aus, das Sie installieren möchten.

   ![Aktualisieren von Visual Studio 2017 mithilfe des Benachrichtigungshubs](media/vs-install-notifications-hub-15dot6.png "Der Benachrichtigungshub in Visual Studio 2017")

      > [!TIP]
      > Da ein Update für eine Edition von Visual Studio 2017 kumulativ ist, wählen Sie immer das mit der aktuellsten Versionsnummer zur Installation aus.

1. Wenn das **Update**-Dialogfeld geöffnet wird, wählen Sie **Jetzt aktualisieren**.

    ![Aktualisieren von Visual Studio 2017 mithilfe des Update-Dialogfelds aus dem Benachrichtigungshub](media/vs-update-now-from-notifications-hub.png "Das Update-Dialogfeld aus dem Benachrichtigungshub in Visual Studio")

     Wenn ein Benutzerzugriffssteuerungs-Dialogfeld geöffnet wird, wählen Sie **Ja**. Als Nächstes könnte ein Dialogfeld „Bitte warten“ einen Moment lang geöffnet werden, und dann wird der Visual Studio-Installer geöffnet, um die Aktualisierung zu starten.

     ![Die neue Benutzeroberfläche von Visual Studio-Installer in Version 15.6](media/visual-studio-15dot6-installer.png "Die neue Benutzeroberfläche von Visual Studio-Installer in Version 15.6")

     Das Update wird fortgesetzt. Wenn es fertig gestellt ist, wird Visual Studio neu startet.

     > [!NOTE]
     > Wenn Sie Visual Studio im Administratormodus ausführen, müssen Sie Visual Studio nach dem Update manuell neu starten.

### <a name="using-the-ide"></a>Verwenden von IDE

Sie können nach einem Update suchen und das Update dann von der Menüleiste in Visual Studio aus installieren.

1. Speichern Sie Ihre Arbeit.

1. Wählen Sie **Hilfe** > **Nach Updates suchen** aus.

     ![Das neue Hilfemenü in Visual Studio Version 15.6](media/vs-help-menu-check-for-updates.png "Das neue Hilfemenü in Visual Studio Version 15.6")

1. Wenn das **Update**-Dialogfeld geöffnet wird, wählen Sie **Jetzt aktualisieren**.

   Das Update wird wie im vorherigen Abschnitt beschrieben durchgeführt, und nachdem das Update erfolgreich abgeschlossen wurde, wird Visual Studio neu gestartet.

   > [!NOTE]
   > Wenn Sie Visual Studio im Administratormodus ausführen, müssen Sie Visual Studio nach dem Update manuell neu starten.

### <a name="using-the-visual-studio-installer"></a>Verwenden des Visual Studio-Installers

Wie in früheren Versionen von Visual Studio können Sie mit dem Visual Studio-Installer ein Update installieren.

1. Speichern Sie Ihre Arbeit.

1. Öffnen Sie den Installer. Der Visual Studio-Installer könnte möglicherweise eine Aktualisierung erfordern, bevor Sie fortfahren.

   > [!NOTE]
   > Auf einem Computer unter Windows 10, finden Sie den Installer unter dem Buchstaben **V** als **Visual Studio-Installer** oder unter dem Buchstaben **M** als **Microsoft Visual Studio-Installer**.

1. Auf der **Produkt**-Seite im Installer suchen Sie nach der Edition von Visual Studio, die Sie installiert haben.

1. Wenn ein Update verfügbar ist, sehen Sie eine Schaltfläche **Update**. (Es kann einige Sekunden dauern, bis der Installer bestimmen kann, ob ein Update verfügbar ist.)

   Klicken Sie auf die Schaltfläche **Aktualisieren**, um die Updates zu installieren.

     ![Aktualisieren von Visual Studio 2017 mithilfe des Visual Studio-Installers](media/update-visual-studio.png "Aktualisieren von Visual Studio 2017 mithilfe des Installers für Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Aktualisieren von Visual Studio 2017 Version 15.5 oder früher

Wenn Sie eine frühere Version verwenden, erfahren Sie hier, wie Sie ein Update auf Visual Studio 2017 Version 15.0 bis Version 15.5 anwenden.

### <a name="update-by-using-the-notifications-hub"></a>Aktualisieren mithilfe des Benachrichtigungshubs

1. Wenn Updates vorhanden sind, wird ein entsprechendes Benachrichtigungsflag in Visual Studio angezeigt.

   ![Visual Studio 2017 mithilfe des Benachrichtigungshubs aktualisieren](media/notification-flag.png "Benachrichtigungsflag für Updates in Visual Studio")

   Klicken Sie auf das Benachrichtigungsflag, um den Hub **Benachrichtigungen** zu öffnen.

   ![Aktualisieren von Visual Studio 2017 mithilfe des Benachrichtigungshub](media/notifications-hub.png "Der Benachrichtigungshub in Visual Studio")

      > [!TIP]
      > Da ein Update für eine Edition von Visual Studio 2017 kumulativ ist, wählen Sie immer das mit der aktuellsten Versionsnummer zur Installation aus.

1. Klicken Sie auf **"Visual Studio Update" is available** („Visual Studio-Update“ steht zur Verfügung), womit das Dialogfeld **Erweiterungen und Updates** geöffnet wird.

   ![Aktualisieren von Visual Studio 2017 mithilfe des Benachrichtigungshub](media/notifications-hub-select.png "Der Benachrichtigungshub in Visual Studio")

1. Klicken Sie im Dialogfeld **Erweiterungen und Updates** auf die Schaltfläche **Update**.

   ![Aktualisieren von Visual Studio 2017 mithilfe des Benachrichtigungshubs](media/notifications-extensions-and-updates.png "Das Dialogfeld „Erweiterungen und Updates“ in Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Weitere Informationen zu Visual Studio-Benachrichtigungen

Visual Studio benachrichtigt Sie, wenn ein Update für Visual Studio selbst oder für eine der Komponenten verfügbar ist und wenn bestimmte Ereignisse in der Visual Studio-Umgebung auftreten.

* Ist das Benachrichtigungsflag gelb, steht ein Visual Studio-Produktupdate für die Installation zur Verfügung.
* Wenn das Benachrichtigungsflag rot ist, gibt es ein Problem mit Ihrer Lizenz.
* Falls das Benachrichtigungsflag schwarz ist, liegen optionale oder informative Nachrichten für Sie bereit.

Klicken Sie auf das Benachrichtigungsflag, um den Hub **Benachrichtigungen** zu öffnen, und klicken Sie dann auf die Benachrichtigungen, die Sie bearbeiten möchten. Alternativ können Sie Benachrichtigungen auch ignorieren oder verwerfen.

 ![Optionale oder informative Nachricht im Benachrichtigungshub anzeigen](media/notification-flag-optional.png "Benachrichtigungsflag für optionale oder informative Nachricht in Visual Studio")

Wenn Sie eine Benachrichtigung ignorieren, wird diese von Visual Studio nicht mehr angezeigt. Wenn Sie die Liste der ignorierten Benachrichtigungen zurücksetzen möchten, wählen Sie im Benachrichtigungshub die Schaltfläche **Einstellungen**.

   ![Schaltfläche „Einstellungen“ im Benachrichtigungshub auswählen, um die Benachrichtigungsoptionen anzuzeigen](media/vs-notifications-hub-settings-button.png "Choose the Settings button in the Notifications hub to view Notification options")

### <a name="update-by-using-the-visual-studio-installer"></a>Aktualisieren mithilfe des Installers für Visual Studio

1. Öffnen Sie den Installer. Möglicherweise müssen Sie den Installer aktualisieren, bevor Sie fortfahren. Ist dies der Fall, werden Sie dazu aufgefordert.

   > [!NOTE]
   > Auf einem Computer unter Windows 10, finden Sie den Installer unter dem Buchstaben **V** als **Visual Studio-Installer** oder unter dem Buchstaben **M** als **Microsoft Visual Studio-Installer**.

1. Auf der **Produkt**-Seite im Installer suchen Sie nach der Edition von Visual Studio, die Sie installiert haben.

1. Wenn ein Update verfügbar ist, sehen Sie eine Schaltfläche **Update**. (Es kann einige Sekunden dauern, bis der Installer bestimmen kann, ob ein Update verfügbar ist.)

   Klicken Sie auf die Schaltfläche **Aktualisieren**, um die Updates zu installieren.

     ![Aktualisieren von Visual Studio 2017 mithilfe des Visual Studio-Installers](media/update-visual-studio.png "Aktualisieren von Visual Studio mithilfe des Visual Studio-Installers")

::: moniker-end

::: moniker range="vs-2019"

Sie sollten ein Update auf die [aktuelle Version](/visualstudio/releases/2019/release-notes/) von Visual Studio 2019 ausführen, damit Sie immer die neuesten Features, Fehlerbehebungen und Verbesserungen erhalten.

> [!IMPORTANT]
> Zum Installieren, Aktualisieren und Anpassen von Visual Studio müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt. Weitere Informationen finden Sie unter [Benutzerberechtigungen und Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Aktualisieren von Visual Studio für Mac](/visualstudio/mac/update).

Hier wird erklärt, wie Sie &nbsp;Studio&nbsp;2019&nbsp;Vorschauversion oder Visual&nbsp;Studio&nbsp;2019&nbsp;RC aktualisieren.

## <a name="use-the-visual-studio-installer"></a>Verwenden des Visual Studio-Installers

1. Öffnen Sie den Installer.

     ![Öffnen des Visual Studio-Installers](media/vs2019-visual-studio-installer.png "Öffnen des Visual Studio-Installers")

   Möglicherweise müssen Sie den Installer aktualisieren, bevor Sie fortfahren. Wenn dies der Fall ist, befolgen Sie die Anweisungen.

1. Suchen Sie im Installer nach der Edition von Visual Studio, die Sie installiert haben.

   Wenn Sie zum Beispiel zuvor Visual&nbsp;Studio Community&nbsp;2019&nbsp;RC installiert haben und es ein Update dafür gibt, wird im Installer die Meldung **Update verfügbar** angezeigt.

     ![Auswählen der Edition von Visual Studio 2019, die Sie aktualisieren möchten](media/vs2019-update-visual-studio-community-rc.png "Auswählen der Edition von Visual Studio 2019, die Sie aktualisieren möchten")

1. Klicken Sie auf die Schaltfläche **Update**, um die Updates zu installieren.

    ![Auswählen der Schaltfläche „Aktualisieren“ zum Installieren der Updates](media/vs2019-choose-update-visual-studio-community-rc.png "Auswählen der Schaltfläche „Aktualisieren“ zum Installieren der Updates")

1. Wählen Sie nach dem Abschluss des Updates **Starten** aus, um Visual Studio zu starten.

    ![Auswählen der Schaltfläche „Starten“ zum Starten von Visual Studio](media/vs2019-choose-launch-visual-studio-community-rc.png "Auswählen der Schaltfläche „Starten“ zum Starten von Visual Studio")

## <a name="use-the-ide"></a>Verwenden der IDE

Sie können nach einem Update suchen und es dann von der Menüleiste oder dem Suchfeld in Visual Studio 2019 aus installieren.

### <a name="open-visual-studio"></a>Öffnen Sie Visual Studio.

1. Wählen Sie im **Windows-Startmenü** **Visual Studio 2019** aus.

    ![Öffnen von Visual Studio 2019 RC](media/vs2019-visual-studio-rc.png "Öffnen von Visual Studio 2019 unter Windows")

1. Wählen Sie unter **Erste Schritte** eine beliebige Option aus, um die IDE zu öffnen.

    ![Öffnen des Visual Studio-Installers](media/vs2019-choose-option-from-get-started.png "Öffnen des Visual Studio-Installers")

    Visual Studio wird geöffnet. In der IDE wird eine Meldung **Visual Studio 2019 Update** angezeigt.

    ![Meldung „Visual Studio 2019 Update“ in der IDE](media/vs2019-update-visual-studio-ide-message.png "Meldung „Visual Studio 2019 Update“ in der IDE")

1. Wählen Sie in der Meldung **Visual Studio 2019 Update** **Details anzeigen** aus.

   ![Auswählen der Schaltfläche „Details anzeigen“ in der IDE-Meldung „Visual Studio 2019 Update“](media/vs2019-update-visual-studio-ide-view-details.png "Auswählen der Schaltfläche „Details anzeigen“ in der Meldung „Visual Studio 2019 Update“")

1. Wählen Sie im Dialogfeld **Das Update wurde heruntergeladen und ist installationsbereit.** **Update** aus.

     ![Auswählen der Schaltfläche „Update“ im Dialogfeld „Das Update wurde heruntergeladen und ist installationsbereit“](media/vs2019-update-visual-studio-community-rc-from-ide.png "Auswählen der Schaltfläche „Update“ im Dialogfeld „Das Update wurde heruntergeladen und ist installationsbereit“")

   Visual Studio wird aktualisiert, geschlossen und anschließend wieder geöffnet.

### <a name="in-visual-studio"></a>In Visual Studio

1. Wählen Sie in der Menüleiste **Hilfe** und dann **Nach Updates suchen** aus.

     ![Auswählen von „Nach Updates suchen“ im Menü „Hilfe“](media/vs-2019/vs-ide-check-updates-help-menu.png "Auswählen von „Nach Updates suchen“ im Menü „Hilfe“")

    > [!NOTE]
    > Sie können auch das Suchfeld in der IDE verwenden, um nach Updates zu suchen. Drücken Sie **STRG**+**Q**, geben Sie „Nach Updates suchen“ ein, und wählen Sie dann das passende Suchergebnis aus.

1. Wählen Sie im Dialogfeld **Das Update wurde heruntergeladen und ist installationsbereit.** **Update** aus.

     ![Auswählen der Schaltfläche „Update“ im Dialogfeld „Das Update wurde heruntergeladen und ist installationsbereit“](media/vs2019-update-visual-studio-community-rc-from-ide.png "Auswählen der Schaltfläche „Update“ im Dialogfeld „Das Update wurde heruntergeladen und ist installationsbereit“")

   Visual Studio wird aktualisiert, geschlossen und anschließend wieder geöffnet.

## <a name="use-the-notifications-hub"></a>Verwenden des Benachrichtigungshubs

1. Speichern Sie Ihre Arbeit in Visual Studio.

1. Wählen Sie das Benachrichtigungssymbol in der unteren rechten Ecke der Visual Studio-IDE aus, um den **Benachrichtigungshub** zu öffnen.

   ![Das Benachrichtigungssymbol in der Visual Studio-IDE](media/vs-2019/notification-bar.png "Das Benachrichtigungssymbol in der Visual Studio-IDE")

1. Wählen Sie im **Benachrichtigungshub** das Update, das Sie installieren möchten, und dann **Details anzeigen** aus.

     ![Der Benachrichtigungshub in Visual Studio 2019](media/vs-2019/notification-hub-update.png "Der Benachrichtigungshub in Visual Studio 2019")

      > [!TIP]
      > Da ein Update für eine Edition von Visual Studio 2019 kumulativ ist, wählen Sie immer das mit der aktuellsten Versionsnummer zur Installation aus.

1. Wählen Sie im Dialogfeld **Das Update wurde heruntergeladen und ist installationsbereit.** **Update** aus.

   Visual Studio wird aktualisiert, geschlossen und anschließend wieder geöffnet.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualisieren von Visual Studio für Mac](/visualstudio/mac/update)
* [Ändern von Visual Studio](modify-visual-studio.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)

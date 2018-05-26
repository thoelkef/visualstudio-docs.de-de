---
title: Bereitstellen von lokalen Ordner
description: Bereitstellen einer app in einen lokalen Ordner
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: bd477fec033eb75f626401586abfd10c798601ef
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2018
---
1. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **veröffentlichen** (für Web Forms, **Web-App veröffentlichen**).

    Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben die **veröffentlichen** Bereich wird angezeigt. Klicken Sie auf **neues Profil**.

1. In der **veröffentlichen** wählen Sie im Dialogfeld **Ordner**, klicken Sie auf **Durchsuchen**, und erstellen Sie einen neuen Ordner **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Wählen Sie für eine Web Forms-app **benutzerdefinierte** Geben Sie im Dialogfeld "Veröffentlichen" einen Profilnamen ein, und wählen Sie **OK**.

1. Klicken Sie auf **Profil erstellen** in der Dropdown-Liste (**veröffentlichen** ist der Standardwert).

1. In der **veröffentlichen** (Dialogfeld), klicken Sie auf die **Einstellungen** verknüpfen, und wählen Sie dann die **Einstellungen** Registerkarte.

1. Legen Sie die Konfiguration auf **Debuggen**Option **alle vorhandenen Dateien vor der Veröffentlichung löschen**, und klicken Sie dann auf **speichern**.

    > [!NOTE]
    > Wenn Sie einen Releasebuild verwenden, deaktivieren Sie das Debuggen in der Datei "Web.config" bei der Veröffentlichung.

1. Klicken Sie auf **Veröffentlichen**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    Die Anwendung veröffentlicht eine **Debuggen** Konfiguration des Projekts, um den lokalen Ordner. Fortschritt zeigt im Ausgabefenster angezeigt.

1. Kopieren Sie das ASP.NET-Projektverzeichnis vom Visual Studio-Computer in das lokale Verzeichnis für die ASP.NET app konfiguriert wurde (in diesem Beispiel **C:\Publish**) auf dem Windows Server-Computer. In diesem Lernprogramm gehen wir davon aus, Sie manuell kopieren, aber Sie können andere Tools, z. B. PowerShell, Xcopy oder Robocopy verwenden.

    > [!CAUTION]
    >  Wenn Sie den Code oder Rebuild ändern müssen, müssen Sie erneut veröffentlichen, und wiederholen Sie diesen Schritt. Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.    Wenn Sie dies nicht tun Sie erhalten eine `cannot find or open the PDB file` Warnung in Visual Studio, wenn Sie versuchen, den Prozess zu debuggen.

1. Stellen Sie sicher, dass Sie die app ordnungsgemäß ausführen können, indem die app in Ihrem Browser öffnen, auf dem Windows Server.

    Falls die Anwendung ordnungsgemäß ausgeführt wird, gibt es möglicherweise ein Konflikt zwischen der Version von ASP.NET auf dem Server und Visual Studio-Computer installiert, oder Sie möglicherweise ein Problem bei der Konfiguration von IIS oder die Website. Überprüfen Sie die bereits beschriebenen Schritte.

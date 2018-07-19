---
title: Bereitstellen in lokalen Ordner
description: Bereitstellen einer app in einen lokalen Ordner
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: bd477fec033eb75f626401586abfd10c798601ef
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809447"
---
1. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **veröffentlichen** (für Web Forms, **Web-App veröffentlichen**).

    Wenn Sie Veröffentlichungsprofile, zuvor konfiguriert haben die **veröffentlichen** angezeigt. Klicken Sie auf **neues Profil**.

1. In der **veröffentlichen** wählen Sie im Dialogfeld **Ordner**, klicken Sie auf **Durchsuchen**, und erstellen Sie einen neuen Ordner **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Wählen Sie für eine Web Forms-app **benutzerdefinierte** veröffentlichungsdialogfeld, geben Sie einen Profilnamen ein, und wählen Sie **OK**.

1. Klicken Sie auf **Profil erstellen** in der Dropdown-Liste (**veröffentlichen** ist der Standardwert).

1. In der **veröffentlichen** Dialogfeld klicken Sie auf die **Einstellungen** verknüpfen, und wählen Sie dann die **Einstellungen** Registerkarte.

1. Legen Sie die Konfiguration auf **Debuggen**Option **löscht alle vorhandenen Dateien vor der Veröffentlichung**, und klicken Sie dann auf **speichern**.

    > [!NOTE]
    > Wenn Sie einen Releasebuild verwenden, deaktivieren Sie das Debuggen in der Datei "Web.config", bei der Veröffentlichung.

1. Klicken Sie auf **Veröffentlichen**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    Die Anwendung veröffentlicht ein **Debuggen** Konfiguration des Projekts zum lokalen Ordner. Fortschritt zeigt im Ausgabefenster angezeigt.

1. Kopieren Sie das ASP.NET-Projektverzeichnis vom Visual Studio-Computer das lokale Verzeichnis für die ASP.NET-App). konfiguriert (in diesem Beispiel **C:\Publish**) auf dem Windows Server-Computer. In diesem Tutorial gehen wir davon aus, Sie manuell kopieren, jedoch können Sie andere Tools wie PowerShell, Xcopy oder Robocopy.

    > [!CAUTION]
    >  Wenn Sie den Code oder die Neuerstellung ändern möchten, müssen Sie erneut veröffentlichen und wiederholen Sie diesen Schritt. Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.    Wenn Sie dies nicht tun Sie erhalten eine `cannot find or open the PDB file` Warnung in Visual Studio, wenn Sie versuchen, den Prozess zu debuggen.

1. Stellen Sie sicher, dass die app ordnungsgemäß ausgeführt werden kann die app in Ihrem Browser zu öffnen, auf dem Windows-Server.

    Wenn die app nicht ordnungsgemäß ausgeführt wird, gibt es möglicherweise ein Konflikt zwischen der Version von ASP.NET auf dem Server und Visual Studio-Computer installiert, oder Sie möglicherweise ein Problem bei der Konfiguration von IIS oder einer Website. Überprüfen Sie die vorherigen Schritten beschrieben.

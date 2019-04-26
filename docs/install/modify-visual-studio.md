---
title: Ändern von Visual Studio 2017
titleSuffix: ''
description: Erfahren Sie Schritt für Schritt, wie Sie Visual Studio ändern.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 03/30/2018
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a08a14d8d07248efdcac759852a38777745e9a51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951563"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Ändern von Visual Studio durch Hinzufügen oder Entfernen von Arbeitsauslastungen und Komponenten

::: moniker range="vs-2019"

Es ist einfach, Visual Studio so anzupassen, dass nur das enthalten ist, was Sie möchten, wenn Sie es möchten. Hierzu öffnen Sie den Visual Studio-Installer, um Workloads und Komponenten hinzuzufügen oder zu entfernen.

::: moniker-end

::: moniker range="vs-2017"

Wir haben nicht nur das Personalisieren von Visual Studio erleichtert, um den Dienst entsprechend Ihren Aufgaben einzurichten, sondern auch die generelle Anpassung von Visual Studio. Hierzu starten Sie den neuen Visual Studio-Installer und nehmen die gewünschten Änderungen vor.

::: moniker-end

Gehen Sie folgendermaßen vor:

## <a name="modify-workloads"></a>Ändern von Arbeitsauslastungen

 Arbeitsauslastungen enthalten die Features, die Sie für die verwendete Programmiersprache oder Plattform benötigen. Verwenden Sie Arbeitsauslastungen, um Visual Studio so zu ändern, dass die Arbeit, die Sie ausführen möchten zum gewünschten Zeitpunkt unterstützt werden.

>[!IMPORTANT]
>Zum Installieren, Aktualisieren und Anpassen von Visual Studio müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt. Weitere Informationen finden Sie unter [Benutzerberechtigungen und Visual Studio](../ide/user-permissions-and-visual-studio.md).

::: moniker range="vs-2017"

1. Suchen Sie den Visual Studio-Installer auf Ihrem Computer.

     Auf einem Computer mit Windows 10 wählen Sie beispielsweise **Start** und blättern dann zum Buchstaben **V**, wo das Installationsprogramm als **Visual Studio-Installer** angezeigt wird.

     ![Visual Studio-Installer](media/vs2017-locate-the-visual-studio-installer.PNG "Suchen des Microsoft Visual Studio-Installers")

     >[!NOTE]
     >Auf manchen Computern ist der Visual Studio-Installer unter dem Buchstaben **„M“** als **Microsoft Visual Studio-Installer** aufgelistet.<br/><br/> Alternativ dazu finden Sie den Visual Studio-Installer in folgendem Speicherort: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Starten Sie das Installationsprogramm, indem Sie darauf klicken oder tippen, und wählen Sie dann **Ändern**.

     ![Starten oder Ändern von Visual Studio](media/modify-visual-studio.png "Ändern von Visual Studio 2017")

     Bei einem ausstehenden Update befindet sich die Schaltfläche „Ändern“ an einer anderen Stelle. Auf diese Weise können Sie bei Bedarf Visual Studio ohne Aktualisierung ändern. Klicken Sie auf **Mehr**, und wählen Sie dann **Ändern**.

     ![Aktualisieren oder Ändern von Visual Studio](media/modify-or-update-visual-studio.png "Aktualisieren oder Ändern von Visual Studio 2017")

1. Aktivieren oder deaktivieren Sie auf dem Bildschirm **Arbeitsauslastungen** die Arbeitsauslastungen, die Sie installieren bzw. deinstallieren möchten.

    ![Visual Studio 2017-Setupdialogfeld](media/vs2017-modify-workloads.PNG "Auswählen einer Arbeitsauslastung in Visual Studio 2017")

1. Wählen Sie erneut **Ändern**.

1. Nachdem die neuen Arbeitsauslastungen und Komponenten installiert wurden, wählen Sie **Starten**.

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

1. Suchen Sie im Installer nach der Edition von Visual Studio, die Sie installiert haben, und klicken Sie dann auf **Ändern**.

     ![Aktualisieren oder Ändern von Visual Studio](media/vs-2019/vs-installer-modify.png "Aktualisieren oder Ändern von Visual Studio 2017")

1. Wählen Sie auf der Registerkarte **Workloads** die Workloads aus oder ab, die Sie installieren bzw. deinstallieren möchten.

    ![Visual Studio 2019-Setupdialogfeld](media/vs-2019/vs-installer-modify-workloads.png "Auswählen einer Workload in Visual Studio 2019")

1. Wählen Sie aus, ob Sie die Standardoption **Beim Herunterladen installieren** oder die Option **Alle herunterladen und dann installieren** verwenden möchten.

    ![Visual Studio 2019-Setupoptionen](media/vs-2019/vs-installer-choose-install-or-download.png "Auswählen von „Beim Herunterladen installieren“ oder „Alle herunterladen und dann installieren“")

    Die Option „Alle herunterladen und dann installieren“ ist praktisch, wenn Sie zuerst alle Dateien herunterladen und die Installation später durchführen möchten.

1. Klicken Sie auf **Ändern**.

1. Klicken Sie im Visual Studio-Installer auf **Starten**, nachdem die neuen Workloads und Komponenten installiert wurden.

::: moniker-end

## <a name="modify-individual-components"></a>Ändern einzelner Komponenten

Wenn Sie keine Workloads installieren möchten, um Ihre Visual Studio-Installation anzupassen, wählen Sie die Registerkarte **Einzelne Komponenten** im Visual Studio-Installer aus, wählen Sie die gewünschten Komponenten aus, und folgen Sie den Anweisungen.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Visual Studio aktualisieren](update-visual-studio.md)
* [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)

---
title: Ändern von Visual Studio 2017
titleSuffix: ''
description: Erfahren Sie Schritt für Schritt, wie Sie Visual Studio ändern.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 06/12/2018
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
ms.openlocfilehash: 03dbfd8140249a93dfb649894dabab1c57b203c2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "57984000"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Ändern von Visual Studio durch Hinzufügen oder Entfernen von Arbeitsauslastungen und Komponenten

Wir haben nicht nur das Personalisieren von Visual Studio erleichtert, um den Dienst entsprechend Ihren Aufgaben einzurichten, sondern auch die generelle Anpassung von Visual Studio. Hierzu starten Sie den neuen Visual Studio-Installer und nehmen die gewünschten Änderungen vor.

Gehen Sie folgendermaßen vor:

## <a name="modify-workloads"></a>Ändern von Arbeitsauslastungen

 Arbeitsauslastungen enthalten die Features, die Sie für die verwendete Programmiersprache oder Plattform benötigen. Verwenden Sie Arbeitsauslastungen, um Visual Studio so zu ändern, dass die Arbeit, die Sie ausführen möchten zum gewünschten Zeitpunkt unterstützt werden.

>[!IMPORTANT]
>Zum Installieren, Aktualisieren und Anpassen von Visual Studio müssen Sie sich mit einem Konto anmelden, das über Administratorberechtigungen verfügt. Weitere Informationen finden Sie unter [Benutzerberechtigungen und Visual Studio](../ide/user-permissions-and-visual-studio.md).

1. Suchen Sie den Visual Studio-Installer auf Ihrem Computer.

     Auf einem Computer mit Windows 10 wählen Sie beispielsweise **Start** und blättern dann zum Buchstaben **V**, wo das Installationsprogramm als **Visual Studio-Installer** angezeigt wird.

     ![Visual Studio-Installer](media/vs2017-locate-the-visual-studio-installer.PNG "Suchen des Microsoft Visual Studio-Installers")

     >[!NOTE]
     >Auf manchen Computern ist der Visual Studio-Installer unter dem Buchstaben **„M“** als **Microsoft Visual Studio-Installer** aufgelistet.<br/><br/> Alternativ dazu finden Sie den Visual Studio-Installer in folgendem Speicherort: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

2. Starten Sie das Installationsprogramm, indem Sie darauf klicken oder tippen, und wählen Sie dann **Ändern**.

     ![Starten oder Ändern von Visual Studio](media/modify-visual-studio.png "Ändern von Visual Studio 2017")

     Bei einem ausstehenden Update befindet sich die Schaltfläche „Ändern“ an einer anderen Stelle. Auf diese Weise können Sie bei Bedarf Visual Studio ohne Aktualisierung ändern. Klicken Sie auf **Mehr**, und wählen Sie dann **Ändern**.

     ![Aktualisieren oder Ändern von Visual Studio](media/modify-or-update-visual-studio.png "Aktualisieren oder Ändern von Visual Studio 2017")

3. Aktivieren oder deaktivieren Sie auf dem Bildschirm **Arbeitsauslastungen** die Arbeitsauslastungen, die Sie installieren bzw. deinstallieren möchten.

    ![Visual Studio 2017-Setupdialogfeld](media/vs2017-modify-workloads.PNG "Auswählen einer Arbeitsauslastung in Visual Studio 2017")

4. Wählen Sie erneut **Ändern**.

5. Nachdem die neuen Arbeitsauslastungen und Komponenten installiert wurden, wählen Sie **Starten**.

## <a name="modify-individual-components"></a>Ändern einzelner Komponenten

Wenn Sie das praktische Arbeitsauslastungsfeature zum Anpassen Ihrer Visual Studio-Installation nicht verwenden möchten, wählen Sie im Visual Studio-Installer die Option **Einzelne Komponenten** und dann die gewünschten Komponenten aus, und folgen Sie den Anweisungen.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Visual Studio aktualisieren](update-visual-studio.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)

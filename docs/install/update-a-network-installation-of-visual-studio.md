---
title: Aktualisieren einer netzwerkbasierten Installation von Visual Studio | Microsoft-Dokumentation
description: '{{PLATZHALTER}}'
ms.date: 05/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 75c65d75ab751058ac435d62f253ead149ccfe42
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aktualisieren einer netzwerkbasierten Installation von Visual Studio

Es ist möglich, ein Layout für die Netzwerkinstallation von Visual Studio mit den neuesten Produktupdates zu aktualisieren, sodass es sowohl als Installationspfad für das neueste Update von Visual Studio auch zum Warten von Installationen verwendet werden kann, die bereits auf Clientarbeitsstationen bereitgestellt wurden.

## <a name="how-to-update-a-network-layout"></a>Gewusst wie: Aktualisieren eines Netzwerklayouts
Um die Netzwerkinstallationsfreigabe so zu aktualisieren, dass sie die neuesten Updates aufweist, führen Sie denselben Befehl `--layout` aus, den Sie bei der erstmaligen Erstellung des Layouts ausgeführt haben, um aktualisierte Pakete schrittweise herunterzuladen.

Wenn Sie beim ersten Erstellen des Netzwerklayouts ein Teillayout ausgewählt haben, vergewissern Sie sich, dass Sie dieselben Befehlszeilenparameter wählen, die Sie beim ersten Erstellen des Layouts für die Netzwerkinstallation verwendet haben (d. h. dieselben Workloads und Sprachen). Bei Wahl anderer Optionen werden mit dem zweiten Befehl `--layout` keine Pakete aktualisiert, die beim zweiten Mal nicht angegeben waren.

Wenn Sie ein Layout in einer Dateifreigabe hosten, wird empfohlen, dass Sie eine private Kopie des Layouts aktualisieren (z. B. `c:\vs2017offline`) und diese, nachdem alle aktualisierten Inhalte heruntergeladen wurden, in Ihre Dateifreigabe kopieren (z. B. `\\server\products\VS2017`).  Wenn Sie dies nicht tun, ist es wahrscheinlicher, dass Benutzer, die das Setup ausführen, während das Layout aktualisiert wird, nicht alle Inhalte aus dem Layout erhalten, da es nicht vollständig aktualisiert wurde.

## <a name="how-to-deploy-an-update-to-client-machines"></a>Gewusst wie: Bereitstellen eines Updates auf Clientcomputern
Je nach Konfiguration Ihrer Netzwerkumgebung kann ein Update entweder von einem Unternehmensadministrator bereitgestellt oder auf einem Clientcomputer ausgelöst werden. 

- Benutzer können eine Instanz von Visual Studio aktualisieren, die über einen Offlineinstallationsordner installiert wurde:
  - Führen Sie den Visual Studio-Installer aus.
  - Klicken Sie auf **Aktualisieren**.

- Administratoren können Clientbereitstellungen von Visual Studio ohne Benutzereingriff mit zwei separaten Befehlen aktualisieren:
  - Aktualisieren Sie zunächst den Visual Studio-Installer: <br>```vs_enterprise.exe --quiet --update```
  - Aktualisieren Sie anschließend die Visual Studio-Anwendung selbst: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> Verwenden Sie den Befehl [vswhere.exe](tools-for-managing-visual-studio-instances.md), um den Installationspfad einer vorhandenen Instanz von Visual Studio auf einem Clientcomputer zu bestimmen.

> [!TIP]
> Weitere Informationen dazu, wie Sie steuern, wann Updatebenachrichtigungen Benutzern angezeigt werden, finden Sie unter [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md).


## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
* [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)


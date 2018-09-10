---
title: Ändern der Installationspfade in Visual Studio 2017
description: Erfahren Sie, wie Sie den Speicherbedarf für die Installation auf dem Systemlaufwerk reduzieren können, indem Sie den Downloadcache, die freigegebenen Komponenten, die SDKs und die Tools auf verschiedene Laufwerke verteilen.
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- move installation files to different drives
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87698421c4992d0349e04740c120d491aa54fcc3
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138965"
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>Ändern der Installationspfade in Visual Studio 2017

**Neu in 15.7:** Der Installationsspeicherbedarf auf dem Systemlaufwerk wurde reduziert, indem der Downloadcache, freigegebene Komponenten, einige SDKs und Tools auf unterschiedliche Datenträger verteilt wurden.

Gehen Sie folgendermaßen vor:

1. Klicken Sie auf die Registerkarte **Installationsoptionen**, wenn Sie Visual Studio installieren.

  ![Visual Studio 2017: Ändern des Installationspfads](media/installation-options-by-location.png "Ändern des Installationspfads")

  > [!IMPORTANT]
  > Wenn Sie die Installation anhalten und später fortsetzen, fährt Visual Studio an der Stelle fort, an der diese unterbrochen wurde. Der Installationsvorgang führt also die übrigen Downloads und Installationen durch und beginnt nicht bei der vorherigen Anzahl.

2. Übernehmen Sie im Abschnitt **Visual Studio-IDE** die Standardeinstellungen. Dadurch wird das Hauptprodukt mit den Dateien installiert, die für diese Version von Visual Studio spezifisch sind.

 > [!IMPORTANT]
 > Wenn es sich bei Ihrem Systemlaufwerk um einen SSD-Datenträger handelt, wird aus folgendem Grund empfohlen, den Standardpfad auf Ihrem Systemlaufwerk zu übernehmen: Wenn Sie mit Visual Studio entwickeln, werden viele Dateien gelesen und geschrieben, wodurch die E/A-Aktivitäten des Laufwerks erhöht werden.  Sie sollten daher ihr schnellstes Laufwerk auswählen, um diese Auslastung zu bewältigen.

2. Wählen Sie im Abschnitt **Downloadcache** aus, ob Sie den Downloadcache beibehalten möchten, und aktivieren oder deaktivieren Sie das Kontrollkästchen **Keep download cache** (Downloadcache beibehalten) entsprechend. <br><br>Wenn Sie den Downloadcache nicht beibehalten möchten, wird der Speicherort nur vorübergehend verwendet. Diese Aktion wirkt sich ebenfalls nicht auf Dateien aus vorherigen Installationen aus oder löscht diese. (Wenn Sie alle Installationspakete löschen möchten, müssen Sie die vorherigen Installationen separat bearbeiten.)

3. Geben Sie im Abschnitt **Downloadcache** das Laufwerk an, auf dem die Installationsdateien und Manifeste gespeichert werden sollen. <br><br>Wenn Sie beispielsweise die Workload „Desktopentwicklung mit C++“ auswählen, ist temporär ein Speicherplatz von 1,58 GB auf Ihrem Systemlaufwerk erforderlich. Dieser wird nach Abschluss der Installation freigegeben.

 > [!NOTE]
 > Die Dateien werden zunächst in einen temporären Ordner auf Ihrem Systemlaufwerk heruntergeladen und später gelöscht, nachdem Visual Studio diese überprüft und in den Ordner für den Downloadcache verschoben hat. Wenn Sie den Downloadcache auf einem anderen Laufwerk beibehalten möchten, benötigt Visual Studio dennoch den Speicherplatz, der der Größe des Downloadcaches auf Ihrem Systemlaufwerk entspricht.
 > [!IMPORTANT]
 > Der Speicherort wird bei der ersten Installation festgelegt und kann im Nachhinein nicht über die Benutzeroberfläche des Installers geändert werden. Sie müssen [Befehlszeilenparameter](use-command-line-parameters-to-install-visual-studio.md) verwenden, um den Downloadcache zu verschieben.

4. Geben Sie im Abschnitt **Freigegebene Komponenten, Tools und SDKs** das Laufwerk an, auf dem Sie Dateien speichern möchten, die von parallelen Installationen von Visual Studio freigegeben werden. SDKs und Tools, durch die der Visual Studio-Installer den Installationspfad ändern kann, werden ebenfalls in diesem Verzeichnis gespeichert.

 > [!NOTE]
 > Es gibt einige Tools und SDKs, für die andere Regeln dafür gelten, an welchem Speicherort sie installiert werden können. Diese Tools und SDKs werden auf Ihrem Systemlaufwerk installiert, auch wenn Sie einen anderen Speicherort auswählen.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio 2017](install-visual-studio.md)
* [Aktualisieren von Visual Studio 2017](update-visual-studio.md)
* [Ändern von Visual Studio 2017](update-visual-studio.md)
* [Deinstallieren von Visual Studio 2017](uninstall-visual-studio.md)

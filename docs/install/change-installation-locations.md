---
title: Auswählen von Installationspfaden
description: Erfahren Sie, wie Sie den Speicherbedarf für die Installation von Visual Studio auf dem Systemlaufwerk reduzieren können, indem Sie den Downloadcache, die freigegebenen Komponenten, die SDKs und die Tools auf verschiedene Laufwerke verteilen.
ms.date: 11/07/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2acefee22976e061b3feff83b00891037a0f2bbd
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159840"
---
# <a name="select-the-installation-locations-in-visual-studio-2017"></a>Auswählen der Installationspfade in Visual Studio 2017

**Neues in 15.7:** Sie können den Installationsspeicherbedarf von Visual Studio auf Ihrem Systemlaufwerk reduzieren, indem Sie den Speicherort für einige Dateien ändern. Genauer gesagt können Sie verschiedene Speicherorte für den Downloadcache, für freigegebene Komponenten, SDKs und Tools verwenden.

   > [!NOTE]
   > Es gibt einige Tools und SDKs, für die andere Regeln dafür gelten, an welchem Speicherort sie installiert werden können. Diese Tools und SDKs werden auch auf Ihrem Systemlaufwerk installiert, wenn Sie einen anderen Speicherort auswählen.

Sind Sie bereit? Gehen Sie folgendermaßen vor:

1. Klicken Sie beim Installieren von Visual Studio auf die Registerkarte **Installationspfade**.

   ![Visual Studio 2017: Auswählen des Installationspfads](media/vs-installation-locations.png "Auswählen des Installationspfads")

1. Übernehmen Sie im Abschnitt **Visual Studio-IDE** die Standardeinstellungen. Visual Studio installiert das Hauptprodukt sowie die Dateien, die in der spezifischen Version von Visual Studio enthalten sind.

   ![Visual Studio-IDE-Abschnitt der Registerkarte „Installationspfade“](media/vs-installation-locations-ide.png "Akzeptieren des Standardpfads für den Abschnitt „Visual Studio-IDE“ der Registerkarte „Installationspfade“")

   > [!TIP]
   > Wenn es sich bei Ihrem Systemlaufwerk um ein SSD (Solid State Drive) handelt, wird empfohlen, dass Sie den Standardpfad auf Ihrem Systemlaufwerk akzeptieren. Begründung: Bei der Entwicklung mit Visual Studio werden mehrere Dateien gelesen und in diese geschrieben, wodurch die E/A-Aktivität des Datenträgers erhöht wird. Sie sollten daher ihr schnellstes Laufwerk auswählen, um diese Auslastung zu bewältigen.

1. Wählen Sie im Abschnitt **Downloadcache** aus, ob der Downloadcache beibehalten werden soll, und wählen Sie dann aus, wo dessen Dateien gespeichert werden sollen.

     ![Abschnitt „Downloadcache“ der Registerkarte „Installationspfade“](media/vs-installation-locations-cache.png "Auswählen, ob der Downloadcache nach der Installation beibehalten werden soll, und Festlegen des Laufwerks, auf dem Dateien gespeichert werden sollen")

    1. Aktivieren oder deaktivieren Sie die Option **Downloadcache nach der Installation beibehalten**.

       Wenn Sie den Downloadcache nicht beibehalten möchten, wird der Speicherort nur vorübergehend verwendet. Diese Aktion wirkt sich nicht auf Dateien aus vorherigen Installationen aus oder löscht diese.

    1. Legen Sie das Laufwerk fest, auf dem Installationsdateien und Manifeste aus dem Downloadcache gespeichert werden sollen.

        Wenn Sie beispielsweise die Workload „Desktopentwicklung mit C++“ auswählen, ist temporär ein Speicherplatz von 1,58 GB auf Ihrem Systemlaufwerk erforderlich. Dieser wird nach Abschluss der Installation freigegeben.

       > [!IMPORTANT]
       > Dieser Speicherort wird bei der ersten Installation festgelegt und kann im Nachhinein nicht über die Benutzeroberfläche des Installers geändert werden. Sie müssen [Befehlszeilenparameter](use-command-line-parameters-to-install-visual-studio.md) verwenden, um den Downloadcache zu verschieben.

1. Geben Sie im Abschnitt **Freigegebene Komponenten, Tools und SDKs** das Laufwerk an, auf dem Sie Dateien speichern möchten, die von parallelen Installationen von Visual Studio freigegeben werden. SDKs und Tools werden ebenfalls in diesem Verzeichnis gespeichert.

   ![Abschnitt „Freigegebene Komponenten, Tools und SDKs“ der Registerkarte „Installationspfade“](media/vs-installation-locations-shared.png "Festlegen des Speicherorts, in dem freigegebene Komponenten, Tools und SDKs gespeichert werden sollen")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio 2017](install-visual-studio.md)
* [Aktualisieren von Visual Studio 2017](update-visual-studio.md)
* [Ändern von Visual Studio 2017 RC](update-visual-studio.md)
* [Deinstallieren von Visual Studio 2017](uninstall-visual-studio.md)

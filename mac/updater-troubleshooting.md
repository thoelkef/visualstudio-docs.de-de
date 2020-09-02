---
title: Updater enthält Fehler, die beim Abrufen von Informationen auftreten
description: Anweisungen zur Behebung, wenn die Fehlermeldung „Fehler beim Abrufen von Updateinformationen“ in Visual Studio 2019 für Mac angezeigt wird
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75405479"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Problembehandlung: Updater enthält Fehler, die beim Abrufen von Informationen auftreten

In seltenen Fällen kann die Fehlermeldung „Fehler beim Abrufen von Updateinformationen“ angezeigt werden, wenn Sie versuchen, [Visual Studio für Mac zu aktualisieren](update.md). Wenn das geschieht, führen Sie die folgenden Schritte zur Behebung aus:

- Überprüfen Sie Ihre Internetverbindung. Eine Unterbrechung der Verbindung ist die häufigste Ursache für diesen Fehler.
  - Wenn eine Komponente nicht heruntergeladen wird, können Sie auf die Schaltfläche zum Wiederholen neben dem Namen der Komponente klicken, um den Download erneut zu versuchen.
- Starten Sie die IDE neu.
- Wenn diese Fehlermeldung weiterhin angezeigt wird, können Sie auch eine Aktualisierung mithilfe des Installers versuchen, falls sich die **.dmg**-Datei noch auf Ihrem Computer befindet. Sie können ihn aber auch von [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/) herunterladen.
  - Mit dem Installer werden alle installierten Komponenten auf Ihrem Computer aktualisiert.
  - Durch erneutes Ausführen des Installers können Sie auch fehlende Komponenten installieren, die zuvor nicht installiert waren.
- Sie können auch versuchen, zwischengespeicherte Downloads zu löschen, indem Sie diese Datei löschen: `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml`.
- Wenn Sie mit einer älteren Version von Visual Studio für Mac arbeiten, befinden sich unter dem Verzeichnis `VisualStudio` möglicherweise andere Versionsnummern. Löschen Sie die Datei `index.xml` in diesen Pfaden ebenfalls.

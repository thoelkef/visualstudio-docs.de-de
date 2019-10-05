---
title: Updater enthält Fehler, die beim Abrufen von Informationen auftreten
description: Anweisungen zur Behebung, wenn die Fehlermeldung „Fehler beim Abrufen von Updateinformationen“ in Visual Studio 2019 für Mac angezeigt wird
ms.topic: troubleshooting
author: asb3993
ms.author: amburns
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 5ba295defe19c6f3c6c56d5bccc7cc3fa367bb50
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107790"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Problembehandlung: Updater enthält Fehler, die beim Abrufen von Informationen auftreten

In seltenen Fällen kann die Fehlermeldung „Fehler beim Abrufen von Updateinformationen“ angezeigt werden, wenn Sie versuchen, [Visual Studio für Mac zu aktualisieren](update.md). Wenn das geschieht, führen Sie die folgenden Schritte zur Behebung aus:

- Überprüfen Sie Ihre Internetverbindung. Eine Unterbrechung der Verbindung ist die häufigste Ursache für diesen Fehler.
  - Wenn eine Komponente nicht heruntergeladen wird, können Sie auf die Schaltfläche zum Wiederholen neben dem Namen der Komponente klicken, um den Download erneut zu versuchen.
- Starten Sie die IDE neu.
- Wenn diese Fehlermeldung weiterhin angezeigt wird, können Sie auch eine Aktualisierung mithilfe des Installers versuchen, falls sich die **.dmg**-Datei noch auf Ihrem Computer befindet. Sie können ihn aber auch von [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/) herunterladen.
  - Mit dem Installer werden alle installierten Komponenten auf Ihrem Computer aktualisiert.
  - Durch erneutes Ausführen des Installers können Sie auch fehlende Komponenten installieren, die zuvor nicht installiert waren.
- Sie können auch versuchen, zwischengespeicherte Downloads zu löschen, indem Sie diese Datei löschen: `~/Library/Caches/VisualStudio/7.0/TempDownload/index.xml`.

---
title: Updater enthält Fehler, die beim Abrufen von Informationen auftreten
description: Anweisungen zur Behebung, wenn die Fehlermeldung „Fehler beim Abrufen von Updateinformationen“ in Visual Studio 2019 für Mac angezeigt wird
author: asb3993
ms.author: amburns
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 554633b2fc5d47d9cc4824ff9d8bf2febfbcd1f8
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2019
ms.locfileid: "67309627"
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
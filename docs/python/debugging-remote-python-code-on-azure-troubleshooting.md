---
title: Problembehandlung beim Remotedebuggen für Python in Azure
description: Problembehandlung für den Versuch, eine in Azure App Service ausgeführte Python-Anwendung mithilfe von Visual Studio zu debuggen.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f545fa223aa929b79016352e799d112bceddaf1c
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341462"
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Problembehandlung für das Remotedebuggen für Python und Azure

Beim Anfügen an eine [Azure App Service for remote debugging (Azure App Service-Instanz für das Remotedebuggen)](debugging-remote-python-code-on-azure.md) kann in Visual Studio aus folgenden Gründen ein Fehler auftreten:

| Grund | Auflösung |
| --- | --- |
| Auf dem Computer ist nicht Visual Studio 2013 Update 4 oder höher installiert. | Installieren Sie eine geeignete Version von [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). |
| Das in App Service bereitgestellte Projekt entspricht nicht dem geöffneten Projekt in Visual Studio. | Laden Sie das richtige Projekt in Visual Studio. |
| Das Projekt wurde nicht mit der **Debugkonfiguration** bereitgestellt. | Stellen Sie die Anwendung erneut bereit, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste erst auf das Projekt und dann auf **Veröffentlichen** klicken. Stellen Sie auf der Registerkarte **Einstellungen** sicher, dass **Debuggen** als Konfiguration ausgewählt wurde. |
| Die App Service-Instanz wird nicht ausgeführt. | Starten Sie die Instanz über den **Server-Explorer** in Visual Studio oder über das Azure-Portal. |
| Die App Service-Instanz ist nicht für Websockets konfiguriert. | Wechseln Sie zum [Azure-Portal](https://portal.azure.com), navigieren Sie zu App Service, öffnen Sie **Einstellungen** > **Anwendungseinstellungen**, legen Sie **Allgemeine Einstellungen** > **Websockets** auf **Ein** fest, und klicken Sie auf **Speichern**. (Beachten Sie, dass die Optionen für das **Debuggen** auf diesem Blatt *nicht* für das Debuggen von Python gelten.) |
| *web.debug.config* wurde geändert und der Debugproxy deaktiviert. | Löschen Sie die Datei, und veröffentlichen Sie das Projekt erneut in App Service. Dabei erstellt Visual Studio die Datei neu. |

Siehe auch:

- [Azure-Remotedebuggen für Python](debugging-remote-python-code-on-azure.md)

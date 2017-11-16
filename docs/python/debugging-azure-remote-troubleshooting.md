---
title: "Problembehandlung für das Azure-Remotedebuggen für Python in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b723b343-dffb-457e-9af7-ee48c1451e30
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 5f8c27eb0c1360e2bd0fcf0593a8438383b6fd69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Problembehandlung für das Remotedebuggen für Python und Azure

Beim Anfügen an eine [Azure App Service for remote debugging (Azure App Service-Instanz für das Remotedebuggen)](debugging-azure-remote.md) kann in Visual Studio aus folgenden Gründen ein Fehler auftreten:

| Grund | Auflösung |
| --- | --- |
| Auf dem Computer ist nicht Visual Studio 2013 Update 4 oder höher installiert. | Installieren Sie eine geeignete Version von [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| Das in App Service bereitgestellte Projekt entspricht nicht dem geöffneten Projekt in Visual Studio. | Laden Sie das richtige Projekt in Visual Studio. |
| Das Projekt wurde nicht mit der Debugkonfiguration bereitgestellt. | Stellen Sie die Anwendung erneut bereit, indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt klicken und **Veröffentlichen** auswählen. Stellen Sie auf der Registerkarte **Einstellungen** sicher, dass **Debuggen** als Konfiguration ausgewählt wurde. |
| Die App Service-Instanz wird nicht ausgeführt. | Starten Sie die Instanz über den Server-Explorer in Visual Studio oder über das Azure-Portal. |
| Die App Service-Instanz ist nicht für Websockets konfiguriert. | Wechseln Sie zum [Azure-Portal](https://portal.azure.com), navigieren Sie zu Ihrer App Service-Instanz, öffnen Sie das Blatt **Einstellungen > Anwendungseinstellungen**, legen Sie **Allgemeine Einstellungen > Websockets** auf **Ein** fest, und klicken Sie auf **Speichern**. (Beachten Sie, dass die Optionen für das **Debuggen** auf diesem Blatt *nicht* für das Debuggen von Python gelten.) |
| `web.debug.config` wurde geändert und der Debugproxy deaktiviert. | Löschen Sie die Datei, und veröffentlichen Sie das Projekt erneut in App Service. Dabei erstellt Visual Studio die Datei neu. |

Siehe auch:

- [Azure-Remotedebuggen für Python](debugging-azure-remote.md)

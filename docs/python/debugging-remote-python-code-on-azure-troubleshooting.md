---
title: "Problembehandlung für das Azure-Remotedebuggen für Python in Visual Studio | Microsoft-Dokumentation"
description: "Problembehandlung für den Versuch, eine in Azure App Service ausgeführte Python-Anwendung mithilfe von Visual Studio zu debuggen."
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 543358e02f37fffbcc2c3981808fded87a3cb12a
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Problembehandlung für das Remotedebuggen für Python und Azure

Beim Anfügen an eine [Azure App Service for remote debugging (Azure App Service-Instanz für das Remotedebuggen)](debugging-remote-python-code-on-azure.md) kann in Visual Studio aus folgenden Gründen ein Fehler auftreten:

| Grund | Auflösung |
| --- | --- |
| Auf dem Computer ist nicht Visual Studio 2013 Update 4 oder höher installiert. | Installieren Sie eine geeignete Version von [visualstudio.com](https://www.visualstudio.com/downloads/). | 
| Das in App Service bereitgestellte Projekt entspricht nicht dem geöffneten Projekt in Visual Studio. | Laden Sie das richtige Projekt in Visual Studio. |
| Das Projekt wurde nicht mit der Debugkonfiguration bereitgestellt. | Stellen Sie die Anwendung erneut bereit, indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt klicken und **Veröffentlichen** auswählen. Stellen Sie auf der Registerkarte **Einstellungen** sicher, dass **Debuggen** als Konfiguration ausgewählt wurde. |
| Die App Service-Instanz wird nicht ausgeführt. | Starten Sie die Instanz über den Server-Explorer in Visual Studio oder über das Azure-Portal. |
| Die App Service-Instanz ist nicht für Websockets konfiguriert. | Wechseln Sie zum [Azure-Portal](https://portal.azure.com), navigieren Sie zu Ihrer App Service-Instanz, öffnen Sie das Blatt **Einstellungen > Anwendungseinstellungen**, legen Sie **Allgemeine Einstellungen > Websockets** auf **Ein** fest, und klicken Sie auf **Speichern**. (Beachten Sie, dass die Optionen für das **Debuggen** auf diesem Blatt *nicht* für das Debuggen von Python gelten.) |
| `web.debug.config` wurde geändert und der Debugproxy deaktiviert. | Löschen Sie die Datei, und veröffentlichen Sie das Projekt erneut in App Service. Dabei erstellt Visual Studio die Datei neu. |

Siehe auch:

- [Azure-Remotedebuggen für Python](debugging-remote-python-code-on-azure.md)

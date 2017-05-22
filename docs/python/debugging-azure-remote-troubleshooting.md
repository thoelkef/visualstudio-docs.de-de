---
title: "Problembehandlung für das Azure-Remotedebuggen für Python in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b723b343-dffb-457e-9af7-ee48c1451e30
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: f9d9d1bc974e43cdd7d1da2a1468a9b7ef84f44b
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---

# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Problembehandlung für das Remotedebuggen für Python und Azure

Beim Anfügen an eine [Azure App Service-Instanz für das Remotedebuggen](debugging-azure-remote.md) kann in Visual Studio aus folgenden Gründen ein Fehler auftreten:

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


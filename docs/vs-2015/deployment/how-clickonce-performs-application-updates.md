---
title: So führt ClickOnce Anwendungs Updates aus | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2e8a3c1054219bb7d5b0f9a9ef5e710786344e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152831"
---
# <a name="how-clickonce-performs-application-updates"></a>Wie ClickOnce Anwendungsupdates ausführt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce verwendet die Datei Versionsinformationen, die im Bereitstellungs Manifest einer Anwendung angegeben sind, um zu entscheiden, ob die Anwendungs Dateien aktualisiert werden sollen. Nachdem ein Update begonnen hat, verwendet ClickOnce eine Technik namens *dateipatching* , um das redundante herunterladen von Anwendungs Dateien zu vermeiden.  
  
## <a name="file-patching"></a>Dateipatching  
 Beim Aktualisieren einer Anwendung werden von ClickOnce nicht alle Dateien für die neue Version der Anwendung heruntergeladen, es sei denn, die Dateien wurden geändert. Stattdessen werden die Hash Signaturen der Dateien, die im Anwendungs Manifest für die aktuelle Anwendung angegeben sind, mit den Signaturen im Manifest für die neue Version verglichen. Wenn sich die Signaturen einer Datei unterscheiden, wird die neue Version von ClickOnce heruntergeladen. Wenn die Signaturen stimmen, wurde die Datei nicht von einer Version in die nächste geändert. In diesem Fall kopiert ClickOnce die vorhandene Datei und verwendet Sie in der neuen Version der Anwendung. Diese Vorgehensweise verhindert, dass ClickOnce die gesamte Anwendung erneut herunterladen muss, auch wenn sich nur eine oder zwei Dateien geändert haben.  
  
 Das Patchen von Dateien funktioniert auch für Assemblys, die bei Bedarf mit den Methoden und heruntergeladen werden <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> .  
  
 Wenn Sie Visual Studio verwenden, um die Anwendung zu kompilieren, generiert Sie neue Hash Signaturen für alle Dateien, wenn Sie das gesamte Projekt neu erstellen. In diesem Fall werden alle Assemblys auf den Client heruntergeladen, obwohl möglicherweise nur einige wenige Assemblys geändert wurden.  
  
 Das Patchen von Dateien funktioniert nicht für Dateien, die als Daten gekennzeichnet sind und im Datenverzeichnis gespeichert werden. Diese werden immer heruntergeladen, unabhängig von der Hash Signatur der Datei. Weitere Informationen zum Datenverzeichnis finden Sie unter [zugreifen auf lokale und Remote Daten in ClickOnce-Anwendungen](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)

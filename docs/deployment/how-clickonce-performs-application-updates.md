---
title: Wie ClickOnce Anwendungsupdates ausführt | Microsoft-Dokumentation
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 359e3b7135613c930bdf15253fa840e9ce8c3627
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937154"
---
# <a name="how-clickonce-performs-application-updates"></a>Ausführung von Anwendungsupdates durch ClickOnce
ClickOnce verwendet die Dateiversionsinformationen, angegeben im Bereitstellungsmanifest einer Anwendung entscheiden, ob Sie die Dateien der Anwendung zu aktualisieren. Nach Beginn eine Aktualisierung verwendet ClickOnce eine Technik namens *Patchen* vermeiden redundante Herunterladen von Dateien.  
  
## <a name="file-patching"></a>Patchen von Dateien  
 Bei der Aktualisierung einer Anwendung wird ClickOnce nicht alle Dateien für die neue Version der Anwendung heruntergeladen, wenn die Dateien geändert haben. Stattdessen werden die Hashsignaturen, der die angegebenen Dateien in das Anwendungsmanifest für die aktuelle Anwendung für die Signaturen im Manifest für die neue Version verglichen. Wenn eine Datei, die Signaturen unterschiedlich sind, lädt die neue Version von ClickOnce herunter. Wenn die Signaturen übereinstimmen, wurde die Datei nicht von einer Version zur nächsten geändert. ClickOnce wird in diesem Fall kopiert die vorhandene Datei und wird in der neuen Version der Anwendung verwendet. Dadurch wird verhindert, dass ClickOnce müssen in diesem Fall die gesamte Anwendung herunterladen, auch wenn nur ein oder zwei Dateien geändert haben.  
  
 Patchen von Dateien kann auch für Assemblys, die heruntergeladen werden bei Bedarf mit der <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> und <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> Methoden.  
  
 Wenn Sie Visual Studio verwenden, um Ihre Anwendung zu kompilieren, generiert er neue Hashsignaturen für alle Dateien, wenn Sie das gesamte Projekt neu erstellen. In diesem Fall werden alle Assemblys an den Client heruntergeladen werden, jedoch nur ein paar Assemblys möglicherweise geändert.  
  
 Patchen von Dateien funktioniert nicht für Dateien, die als Daten markiert sind, und in das Verzeichnis "Data" gespeichert. Diese werden unabhängig von der Signatur der Datei-Hash immer heruntergeladen. Weitere Informationen zu dem Verzeichnis "Data", finden Sie unter [Zugriff auf lokale und remote-Daten in ClickOnce-Anwendungen](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)
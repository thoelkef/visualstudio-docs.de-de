---
title: Wie ClickOnce Anwendungsupdates ausführt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbe09cfe546d947bf07334e9dd6468226884e9e3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31557696"
---
# <a name="how-clickonce-performs-application-updates"></a>Wie ClickOnce Anwendungsupdates ausführt
ClickOnce verwendet die Dateiversionsinformationen im Bereitstellungsmanifest der Anwendung angegebenen entscheiden, ob Sie die Dateien der Anwendung zu aktualisieren. Nach dem Beginn der Aktualisierung verwendet ClickOnce ein Verfahren namens *Patchen* vermeiden redundante Herunterladen von Dateien.  
  
## <a name="file-patching"></a>Patchen  
 Beim Aktualisieren einer Anwendung wird ClickOnce nicht alle Dateien für die neue Version der Anwendung heruntergeladen, wenn die Dateien geändert haben. Stattdessen vergleicht er die Hashsignaturen der Dateien im Anwendungsmanifest für die aktuelle Anwendung für die Signaturen in das Manifest für die neue Version angegeben. Wenn eine Datei Signaturen unterschiedlich sind, lädt ClickOnce die neue Version. Wenn die Signaturen übereinstimmen, wurde die Datei nicht von einer Version zur nächsten geändert. In diesem Fall ClickOnce die vorhandene Datei kopiert und in die neue Version der Anwendung verwendet. Dieser Ansatz wird verhindert, dass ClickOnce müssen erneut, die gesamte Anwendung herunterladen, auch wenn nur ein oder zwei Dateien geändert wurden.  
  
 Patchen funktioniert auch für Assemblys, die heruntergeladen werden bei Bedarf mit der <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> und <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> Methoden.  
  
 Wenn Sie Visual Studio verwenden, um Ihre Anwendung zu kompilieren, generiert er neue Hashsignaturen für alle Dateien, wenn Sie das gesamte Projekt neu erstellen. In diesem Fall werden alle Assemblys an den Client heruntergeladen werden, jedoch nur einige Assemblys möglicherweise geändert.  
  
 Patchen funktioniert nicht für Dateien, die als Daten gekennzeichnet und im Data-Verzeichnis gespeichert. Diese werden immer unabhängig von der Datei-Hashsignatur heruntergeladen. Weitere Informationen auf das Datenverzeichnis finden Sie unter [zugreifen auf lokale und Remotedaten in ClickOnce-Anwendungen](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen einer Strategie für die ClickOnce-Aktualisierung](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)
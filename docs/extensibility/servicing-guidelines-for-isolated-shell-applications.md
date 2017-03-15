---
title: "Die Wartung von Richtlinien f&#252;r Applikationen isolierte Shell | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Shell integrierten Modus Wartungsfreundlichkeit"
  - "Shell integrierten Modus [Visual Studio] Wartungsfreundlichkeit"
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Die Wartung von Richtlinien f&#252;r Applikationen isolierte Shell
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine Visual Studio isolated Shell\-Anwendung verteilen, müssen Sie sein Bereitstellen von Softwareupdates für die Anwendung nach der Installation. Zu diesem Zweck müssen Sie die Anwendung mithilfe einer Microsoft Installer \(MSI\)\-Datei installieren. Diese Art der Installation kann Softwareupdates von Microsoft Web verteilt werden bereitgestellten herunterladen und Ihre Kunden ohne benutzerdefinierte Eingriff genutzt.  
  
## Wartungsanforderungen  
 Sie können sicherstellen, dass die isolierte Shell\-Installation Updates zulassen kann, um sicherzustellen, dass das Installationsprogramm die folgenden drei Kriterien erfüllt.  
  
### Verteilen Sie, indem Sie eine MSI\-Datei  
 Sie müssen eine MSI\-Datei verwenden, um die Anwendung neu verteilen, da eine MSI\-Datei Produkt Identität behält und sicher, dass stellt die Anwendung eines physischen Speicherorts auf dem Clientcomputer. Mergemodule \(MSM\-Dateien\) enthalten keine solchen Garantien und sollte nicht verwendet werden.  
  
### Buchhaltung für benutzerdefinierte Aktionen  
 Benutzerdefinierte Aktionen sind nicht dem Standard entsprechende Installation Direktiven in ein Installationsprogramm. Benutzerdefinierte Aktionen werden Parameter z. B. Speicherorte, Registrierungseinträge, Einstellungen oder andere Elemente der Installation ändern. Benutzerdefinierte Aktionen möglicherweise Daten während der Installation ändern.  
  
 Wenn Sie benutzerdefinierte Aktionen in einem Installationsprogramm verwenden, müssen Sie sicherstellen, dass jede Installation benutzerdefinierte Aktion muss eine entsprechende benutzerdefinierte Aktion nicht rückgängig gemacht werden, wenn der Benutzer die Anwendung deinstalliert haben. Wenn Ihre Installation fehlschlagen, geben Sie die entsprechende benutzerdefinierte Aktion deinstallieren, verlassen entfernen die Anwendung teilweise installiert.  
  
-   Eine benutzerdefinierte Aktion, die auf eine bestimmte Version einer Datei oder Hash\-Werte beruht schlägt fehl, wenn Softwareupdates ändern diese Versionen oder hash\-Werte. In diesem Fall muss die benutzerdefinierte Aktion diese Werte manuell aktualisieren. Ein zusätzliches Problem tritt auf, wenn Versionen einer Datei oder Hash\-Werte zwischen Versionen von Produkten gemeinsam genutzt werden. Vermeiden Sie diese Abhängigkeit, die möglichst.  
  
### Unter Berücksichtigung der freigegebenen Dateien  
 Freigegebene Dateien haben dieselben Namen und am gleichen Speicherort durch mehrere Produkte installiert sind. Diese Produkte in der Version, Lager halten Unit \(SKU\) oder beides abweichen können, und die Produkte können auf einem Computer koexistieren. Freigegebene Dateien werden jedoch Wartung Probleme verschiedenen Gründen erstellen:  
  
-   Aktualisieren freigegebene Dateien kann Probleme mit der Anwendungskompatibilität dazu führen, dass ein Update für eine Anwendung kann sich ändern der Version einer Datei verwendet, die von einer anderen Anwendung, die nicht aktualisiert wurde. Installationsprogramme für Produkte, die Freigabe von Dateien die Anzahl der Verweise auf die freigegebenen Dateien. Deinstallieren eines Produkts wirkt sich daher nicht auf freigegebene Dateien, die nicht verringern die Anzahl der installierten Instanzen aus.  
  
-   Das Installationsprogramm Quick Fix Engineering \(QFE\) zurückgesetzt Versionen der Dateien zu den Versionen der Produkte, die das QFE\-Installationsprogramm bedient. Dieser Vorgang wird möglicherweise eine Anwendung, die eine aktualisierte freigegebene Datei übermittelte unterbrochen.
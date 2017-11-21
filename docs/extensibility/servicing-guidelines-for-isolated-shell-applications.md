---
redirect_url: shell/servicing-guidelines-for-isolated-shell-applications
title: "Richtlinien für die Wartung isolierte Shell-Anwendungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e15d228794fb03441d42c081f11bf75b11fdd45
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Wartung von Richtlinien für Isolated Shell-Anwendungen
Wenn Sie eine Visual Studio isolated Shell-Anwendung verteilen, müssen Sie möglicherweise für Ihre Anwendung von Softwareupdates bereitstellen, nach der Installation. Zu diesem Zweck müssen Sie die Anwendung mithilfe einer Microsoft Installer (MSI)-Datei installieren. Diese Art der Installation kann Softwareupdates von Microsoft vom Webdienst verteilt werden bereitgestellt herunterladen und Ihre Kunden ohne Zutun des benutzerdefinierten genutzt.  
  
## <a name="servicing-requirements"></a>Wartungsanforderungen  
 Sie können sicherstellen, dass die isolierte Shell-Installation Updates zulassen kann, indem Sie sicherstellen, dass das Installationsprogramm die folgenden drei Kriterien erfüllt.  
  
### <a name="redistribute-by-using-an-msi"></a>Verteilen Sie, indem Sie eine MSI-Datei  
 Sie müssen eine MSI-Datei verwenden, um die Anwendung neu verteilen, da eine MSI-Datei Produkt Identität behält und sicher, dass stellt die Anwendung ein physisches Speicherorts auf dem Clientcomputer verfügt. Mergemodule (MSM-Dateien) bieten keine solche zusicherungen und sollte nicht verwendet werden.  
  
### <a name="accounting-for-custom-actions"></a>Unter Berücksichtigung der benutzerdefinierte Aktionen  
 Benutzerdefinierte Aktionen sind nicht dem Standard entsprechende Installation Direktiven in einem Installationsprogramm. Benutzerdefinierte Aktionen werden die Parameter wie Dateispeicherorte, registrierungseinstellungen, benutzereinstellungen und andere Installationselemente ändern. Benutzerdefinierte Aktionen können Daten bei der Installation manipulieren.  
  
 Wenn Sie benutzerdefinierte Aktionen in einem Installationsprogramm verwenden, müssen Sie sicherstellen, dass jede Installation benutzerdefinierte Aktion muss eine entsprechende benutzerdefinierte Aktion aus, um die Aktion rückgängig zu machen, wenn der Benutzer die Anwendung deinstalliert haben. Wenn Ihr Programm fehlschlägt, geben Sie die entsprechende benutzerdefinierte Aktion deinstallieren, wird Ihre Anwendung entfernt teilweise installiert lassen.  
  
-   Eine benutzerdefinierte Aktion, die auf eine bestimmte Version einer Datei oder einen Hashcode Werte stützt schlägt fehl, wenn Softwareupdates ändern diese Versionen oder hash-Werte. In diesem Fall muss die benutzerdefinierte Aktion diese Werte manuell aktualisieren. Ein zusätzliches Problem tritt auf, wenn Versionen einer Datei oder einen Hashcode Werte Produktversionen gemeinsam genutzt werden. Vermeiden Sie diese Abhängigkeit an, wann immer möglich.  
  
### <a name="accounting-for-shared-files"></a>Unter Berücksichtigung der freigegebenen Dateien  
 Freigegebene Dateien denselben Namen haben und am gleichen Speicherort durch mehrere Produkte installiert sind. Diese Produkte in der Version, Stock Keeping Unit (SKU) oder beides unterscheidet sich möglicherweise, und die Produkte können auf einem Computer koexistieren. Freigegebene Dateien werden jedoch Wartung Probleme verschiedenen Gründen erstellen:  
  
-   Aktualisieren freigegebene Dateien, kann zu Anwendungskompatibilitätsproblemen verursachen, da ein Update für eine Anwendung möglicherweise ändern der Version einer Datei, die von einer zweiten Anwendung, die nicht aktualisiert wurde verwendet. Installationsprogramme für Produkte, die Freigabe von Dateien die Anzahl der Verweise auf die freigegebenen Dateien. Deinstallieren eines Produkts wirkt sich daher nicht auf freigegebene Dateien außerhalb verringern die Anzahl der installierten Instanzen aus.  
  
-   Das Installationsprogramm Quick Fix Engineering (QFE) zurückgesetzt Versionen von Dateien mit den Versionen der Produkte, die das QFE-Installationsprogramm bedient. Dieser Vorgang wird möglicherweise eine Anwendung, die eine aktualisierte freigegebene Datei übermittelte unterbrochen.
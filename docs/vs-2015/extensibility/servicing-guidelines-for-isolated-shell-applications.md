---
title: Wartungsrichtlinien für isolierte Shell-Anwendungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159270"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Wartungsrichtlinien für Anwendungen der isolierten Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine Visual Studio isolated Shell-Anwendung verteilen, müssen Sie möglicherweise geben nach der Installation von Softwareupdates für Ihre Anwendung. Zu diesem Zweck müssen Sie Ihre Anwendung installieren, über eine Microsoft Installer (MSI)-Datei. Diese Art von Installation ermöglicht die Softwareupdates von Microsoft Web verteilt werden bereitgestellt herunterladen und von Ihren Kunden ohne benutzerdefinierte Eingriff genutzt werden.  
  
## <a name="servicing-requirements"></a>Wartungsanforderungen  
 Sie können sicherstellen, dass die isolierte Shell-Installation Updates zulassen kann, indem Sie sicherstellen, dass das Installationsprogramm die drei folgenden Kriterien erfüllt.  
  
### <a name="redistribute-by-using-an-msi"></a>Erneut verteilen Sie, indem Sie eine MSI-Datei  
 Sie müssen eine MSI-Datei verwenden, um die Anwendung neu verteilen, da eine MSI-Datei behält die Produkt-Identität und sicher, dass stellt die Anwendung eines physischen Speicherorts auf dem Clientcomputer. Mergemodule (MSM-Dateien) bieten keine solchen Garantien und sollte nicht verwendet werden.  
  
### <a name="accounting-for-custom-actions"></a>Kontoführung für benutzerdefinierte Aktionen  
 Benutzerdefinierte Aktionen sind nicht dem Standard entsprechende Installation Anweisungen in einem Installationsprogramm. Benutzerdefinierte Aktionen werden die Parameter wie z. B. Speicherorte, registrierungseinstellungen, benutzereinstellungen und andere Installationselemente ändern. Benutzerdefinierte Aktionen möglicherweise Daten bearbeiten, während der Installation.  
  
 Wenn Sie benutzerdefinierte Aktionen in einem Installationsprogramm verwenden, müssen Sie sicherstellen, dass jede benutzerdefinierte Installation-Aktion muss eine entsprechende benutzerdefinierte Aktion rückgängig gemacht werden, wenn der Benutzer die Anwendung deinstalliert haben. Wenn Ihr Programm-Installation schlägt fehl, geben Sie die entsprechende benutzerdefinierte Aktion deinstallieren, verlassen entfernen die Anwendung teilweise installiert.  
  
- Eine benutzerdefinierte Aktion, die auf eine bestimmte Version einer Datei oder einen Hashcode Werte basieren schlägt fehl, wenn Softwareupdates so ändern Sie diese Versionen oder prüfsummenhashwerte. In diesem Fall muss diese Werte von die benutzerdefinierte Aktion manuell aktualisieren. Ein zusätzliches Problem tritt auf, wenn Sie Versionen einer Datei oder einen Hashcode Werte Produktversionen gemeinsam genutzt werden. Vermeiden Sie diese Abhängigkeit an, wann immer möglich.  
  
### <a name="accounting-for-shared-files"></a>Kontoführung für freigegebene Dateien  
 Freigegebene Dateien haben die gleichen Namen und am gleichen Speicherort durch mehrere Produkte installiert sind. Diese Produkte unterscheiden sich in der Version, Lager halten Unit (SKU) oder beides, und die Produkte können gleichzeitig auf einem Computer vorhanden sein. Allerdings erstellen Sie freigegebene Dateien Wartung Probleme verschiedene Ursachen haben:  
  
- Aktualisieren freigegebene Dateien kann die Probleme mit der Anwendungskompatibilität, da ein Update für eine Anwendung ändern kann die Version einer Datei ein, die eine zweite Anwendung, die nicht aktualisiert wurde. Installationsprogramme für Produkte, die Dateifreigabe gezählt, Verweise auf die freigegebenen Dateien. Deinstallieren eines Produkts wirkt sich daher nicht auf freigegebene Dateien über verringern die Anzahl der installierten Instanzen aus.  
  
- Das Installationsprogramm Quick Fix Engineering (QFE) wird die Versionen der Dateien auf die Versionen der Produkte, die das QFE-Installationsprogramm verarbeitet zurückgesetzt. Dieser Prozess wird möglicherweise eine Anwendung, die eine aktualisierte, freigegebene Datei übermittelt haben.

---
title: Wartungsrichtlinien für isolierte Shellanwendungen | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159270"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Wartungsrichtlinien für Anwendungen der isolierten Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine isolierte Visual Studio Shell-Anwendung verteilen, müssen Sie nach der Installation Software Updates für die Anwendung bereitstellen können. Zu diesem Zweck müssen Sie die Anwendung mithilfe einer Microsoft Installer (MSI)-Datei installieren. Bei dieser Art der Installation können von Microsoft bereitgestellte Software Updates durch den Webdownload neu verteilt und von ihren Kunden ohne benutzerdefiniertes Eingreifen genutzt werden.  
  
## <a name="servicing-requirements"></a>Wartungsanforderungen  
 Sie können sicherstellen, dass die isolierte Shell-Installation Updates zulässt, indem Sie sicherstellen, dass das Installationsprogramm die folgenden drei Kriterien erfüllt.  
  
### <a name="redistribute-by-using-an-msi"></a>Neuverteilen mithilfe einer MSI  
 Sie müssen eine MSI-Anwendung verwenden, um die Anwendung neu zu verteilen, da eine MSI die Produktidentität beibehält und sicherstellt, dass die Anwendung über einen physischen Speicherort auf dem Client Computer verfügt. Mergemodule (MSM-Dateien) bieten keine solchen Zusicherungen und sollten nicht verwendet werden.  
  
### <a name="accounting-for-custom-actions"></a>Kontoführung für benutzerdefinierte Aktionen  
 Benutzerdefinierte Aktionen sind nicht dem Standard entsprechende Installations Direktiven in einem Installationsprogramm. Benutzerdefinierte Aktionen ändern Parameter, wie z. b. Dateispeicher Orte, Registrierungs Einstellungen, Benutzereinstellungen oder andere Installations Elemente. Benutzerdefinierte Aktionen können Daten beim Installations Zeitpunkt bearbeiten.  
  
 Wenn Sie benutzerdefinierte Aktionen in einem Installationsprogramm verwenden, müssen Sie sicherstellen, dass jede benutzerdefinierte Installationszeit Aktion eine entsprechende benutzerdefinierte Aktion aufweisen muss, um die Aktion rückgängig zu machen, wenn der Benutzer die Anwendung deinstalliert. Wenn die entsprechende benutzerdefinierte Deinstallations Aktion nicht durch das Installationsprogramm bereitgestellt werden kann, wird das Entfernen der Anwendung teilweise installiert.  
  
- Eine benutzerdefinierte Aktion, die auf einer bestimmten Version einer Datei oder auf Hashwerte basiert, schlägt fehl, wenn diese Versionen oder Hashwerte von Software Updates geändert werden. In diesem Fall muss die benutzerdefinierte Aktion diese Werte manuell aktualisieren. Ein zusätzliches Problem tritt auf, wenn Versionen einer Datei oder von Hash Werten von Produktversionen gemeinsam genutzt werden. Vermeiden Sie diese Abhängigkeit, wenn dies möglich ist.  
  
### <a name="accounting-for-shared-files"></a>Buchhaltung für freigegebene Dateien  
 Freigegebene Dateien haben die gleichen Namen und werden von mehreren Produkten am gleichen Speicherort installiert. Diese Produkte unterscheiden sich möglicherweise in Version, Stock Keeping Unit (SKU) oder beides, und die Produkte können auf einem bestimmten Computer nebeneinander vorhanden sein. Freigegebene Dateien erstellen jedoch aus verschiedenen Gründen Wartungsprobleme:  
  
- Das Aktualisieren von freigegebenen Dateien kann zu Anwendungs Kompatibilitätsproblemen führen, da bei einem Update einer Anwendung möglicherweise die Version einer Datei geändert wird, die von einer zweiten Anwendung verwendet wird, die nicht aktualisiert wurde. Installationsprogramme für Produkte, die Dateifreigaben verwenden, verweisen auf die freigegebenen Dateien. Daher wirkt sich die Deinstallieren eines Produkts nicht auf freigegebene Dateien aus, die über die Herabsetzung der Anzahl installierter Instanzen hinausgehen.  
  
- Der QFE-Installer (Quick Fix Engineering) kehrt Versionen von Dateien auf die Versionen der Produkte zurück, die der QFE-Installer gewartet hat. Dieser Prozess unterbricht möglicherweise eine Anwendung, die eine aktualisierte freigegebene Datei übermittelt hat.

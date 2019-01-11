---
title: VSPackage-Registrierung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1484840998b7834af55b0f9a026b899aea4f3f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868338"
---
# <a name="vspackage-registration"></a>VSPackage-Registrierung
VSPackages müssen empfehlen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , dass diese installiert werden und sollte geladen werden. Dieser Prozess erfolgt durch das Schreiben von Informationen in der Registrierung. Das ist ein typischer Auftrag eines Installationsprogramms.  
  
> [!NOTE]
>  Es ist eine akzeptierte Methode während der Entwicklung von VSPackage selbstregistrierung verwenden. Allerdings [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] Partner darf nicht ihre Produkte mithilfe der Self-Registrierung als Teil des Setups ausgeliefert.  
  
 Registrierungseinträge in einer Windows Installer-Paket werden in der Regel in der Tabelle der Registrierung vorgenommen. Sie können Erweiterungen auch in der Tabelle für die Registrierung registrieren. Windows Installer bietet jedoch integrierten Unterstützung durch den Programmbezeichner (ProgId), Klasse, Erweiterung und Verb-Tabellen. Weitere Informationen finden Sie unter [Datenbanktabellen](/windows/desktop/Msi/database-tables).  
  
 Achten Sie darauf, dass Ihre Einträge in der Registrierung der Komponente zugeordnet sind, die für Ihre gewählte Strategie zur Seite-an-Seite geeignet ist. Registrierungseinträge für eine freigegebene Datei sollte z. B. Windows Installer-Komponente der Datei zugeordnet werden. Auch sollte Registrierungseinträge für eine Datei hängt von der Version dieser Datei der Komponente zugeordnet sein. Andernfalls installieren oder deinstallieren Sie das VSPackage für eine Version der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] konnte Ihr VSPackage in anderen Versionen unterbrechen. Weitere Informationen finden Sie unter [unterstützt mehrere Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Die einfachste Möglichkeit zum Verwalten der Registrierung werden die gleichen Daten in die gleichen Dateien für entwicklerregistrierung und Installation-Registrierung verwenden. Beispielsweise können einige Installer-Entwicklungstools-Datei in der .reg-Format zum Zeitpunkt der Erstellung nutzen. Wenn Entwickler verwalten die reg-Dateien für ihre eigenen tägliche Entwicklung und Debuggen, die gleichen Dateien können im Installer automatisch eingeschlossen. Wenn Sie nicht automatisch Daten freigeben können, müssen Sie sicherstellen, dass des Installationsprogramms, Kopie der Registrierungsdaten aktuell ist.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrieren von nicht verwalteten VSPackages  
 Nicht verwaltete VSPackages (einschließlich der von der Visual Studio-Paketvorlage generierten) verwenden Sie im ATL-Stil RGS-Dateien zum Speichern von Informationen zur produktregistrierung. Das Format der RGS-Datei bezieht sich auf ATL und können nicht in der Regel als genutzt werden – durch eine Installation mit dem authoring-Tool ist. Registrierungsinformationen für das VSPackage-Installationsprogramm muss separat verwaltet werden. Beispielsweise können Entwickler Dateien in der .reg-Format mit RGS dateiänderungen synchronisiert. Reg-Dateien können mit "regedit" zusammengeführt werden, für die Entwicklung oder durch ein Installationsprogramm genutzt werden.  
  
## <a name="registering-managed-vspackages"></a>Registrieren verwaltete VSPackages  
 Das RegPkg-Tool liest die Registrierungsattribute in ein verwaltetes VSPackage und können entweder die Informationen direkt in der Registrierung oder Write-reg-Format-Dateien, die durch ein Installationsprogramm genutzt werden können.  
  
> [!NOTE]
>  Das RegPkg-Tool ist keine weitervertreibbare Komponente verfügbar und kann nicht verwendet werden, um ein VSPackage auf dem System eines Benutzers zu registrieren.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Warum sollten VSPackages nicht bei der Installation registrieren  
 Wenn Sie Ihre VSPackage-Installationsprogramme sollte nicht auf selbstregistrierung verlassen. Auf den ersten Blick scheint eine VSPackage Registrierungswerte beibehalten, nur im VSPackage selbst eine gute Idee. Angesichts der Tatsache, dass Entwickler die Registrierungswerte verfügbar für die routinemäßige Arbeit und testen, es sinnvoll ist, vermeiden, dass eine separate Kopie der Registrierungsdaten im Installer. Das Installationsprogramm kann für das VSPackage zum Schreiben von Registrierungswerten basieren.  
  
 Bei gut in der Theorie hat die selbstregistrierung einige Mängel, die für die VSPackage-Installation nicht mehr geeignet sind:  
  
- Unterstützung von Installation, Deinstallation, Rollback der Installation und Deinstallation Rollback richtig, müssen Sie vier benutzerdefinierte Aktionen für alle verwalteten VSPackage zu erstellen, die selbst werden durch Aufrufen von regpkg entsprechend registriert.  
  
- Ihr Ansatz zur Unterstützung von Seite-an-Seite ist möglicherweise, dass Sie vier benutzerdefinierte Aktionen erstellen, die für jede unterstützte Version von RegSvr32 oder RegPkg Aufrufen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
- Eine Installation mit Self registrierten Module kann nicht sicher zurückgesetzt werden, da es gibt keine Möglichkeit, der anzeigt, ob die Schlüssel selbst registrierten durch eine andere Funktion oder eine Anwendung verwendet werden.  
  
- Selbst registrierten DLLs verknüpft manchmal mit zusätzlichen DLLs, die nicht vorhanden sind, oder die falsche Version. Im Gegensatz dazu können die Windows Installer DLLs, die keine Abhängigkeit von den aktuellen Zustand des Systems mit den Registrierungstabellen registrieren.  
  
- Selbstregistrierungscodes kann verweigert werden, den Zugriff auf Netzwerkressourcen, wie z. B. Bibliotheken, wenn eine Komponente ist sowohl als angegeben ausführen-aus-Source- und finden Sie in der Tabelle SelfReg. Dadurch kann die Installation der Komponente eine Administratorinstallation fehlschlägt.  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Installer](/windows/desktop/Msi/windows-installer-portal)   
 [Managed Package-Registrierung](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
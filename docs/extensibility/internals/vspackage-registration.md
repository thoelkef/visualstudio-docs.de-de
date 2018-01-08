---
title: VSPackage-Registrierung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1405fbeba34f3e3aa9c645f6eaffe90fe6ac9036
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-registration"></a>VSPackage-Registrierung
VSPackages müssen informieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , dass diese installiert werden und sollte geladen werden. Dieser Vorgang erfolgt durch Schreiben von Informationen in der Registrierung. Ein Auftrag mit einem Installationsprogramm typisch ist.  
  
> [!NOTE]
>  Ist eine akzeptierte Methode während der Entwicklung von VSPackage Self-Registrierung verwenden. Allerdings [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] Partner darf nicht ihre Produkte, die mithilfe von Self-Registrierung als Teil des Setups ausgeliefert.  
  
 Registrierungseinträge in einer Windows Installer-Paket werden in der Regel in der Tabelle der Registrierung vorgenommen. Sie können auch Erweiterungen, die in der Tabelle Registrierung registrieren. Windows Installer bietet jedoch die integrierten Unterstützung durch den Programmbezeichner (ProgId), Klasse, Erweiterung und Verb-Tabellen. Weitere Informationen finden Sie unter [Datenbanktabellen](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Achten Sie darauf, dass Ihre Registrierungseinträge der Komponente zugeordnet sind, die für Ihre ausgewählte Seite-an-Seite-Strategie geeignet ist. Beispielsweise sollte Registrierungseinträge für eine freigegebene Datei mit Windows Installer-Komponente in dieser Datei verknüpft sein. Ebenso sollten Registrierungseinträge für eine Datei hängt von der Version dieser Datei Komponente zugeordnet werden. Andernfalls installieren oder deinstallieren Sie das VSPackage für eine Version der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] werden das VSPackage in anderen Versionen möglicherweise funktionsunfähig. Weitere Informationen finden Sie unter [unterstützen mehrere Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Die einfachste Möglichkeit zum Verwalten der Registrierung ist die Verwendung derselben Daten in die gleichen Dateien, die für Entwickler Registrierung und Installationszeit Registrierung. Beispielsweise können einige Installer-Entwicklungstools Datei im reg-Format zur Buildzeit nutzen. Wenn Entwickler reg-Dateien für ihre eigenen täglichen Entwicklung verwalten und Debuggen, dieselben Dateien können im Installationsprogramm automatisch eingeschlossen. Wenn Sie nicht automatisch Registrierungsdaten freigeben können, müssen Sie sicherstellen, dass das Installationsprogramm Kopie der Registrierungsdaten aktuell sind.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrieren die nicht verwaltete VSPackages  
 Nicht verwaltete VSPackages (einschließlich der von der Visual Studio-Paketvorlage generiert) verwenden Sie ATL-Stil RGS-Dateien zum Speichern von Informationen zur produktregistrierung. Das RGS-Dateiformat ist spezifisch für ATL und können nicht in der Regel als genutzt werden – wird durch eine Installation mit dem authoring Tool. Registrierungsinformationen für das VSPackage-Installationsprogramm muss separat verwaltet werden. Beispielsweise können Entwickler Dateien in der .reg-Format mit RGS dateiänderungen synchronisieren. Die reg-Dateien mit RegEdit für Entwicklungen zusammengeführt oder von einem Installationsprogramm genutzt werden.  
  
## <a name="registering-managed-vspackages"></a>Verwaltete VSPackages registrieren  
 Das RegPkg-Tool liest die Registrierungsattribute aus ein verwaltetes VSPackage und können entweder Schreiben der Informationen direkt in der Registrierung oder der Schreibvorgang reg-Format-Dateien, die von einem Installationsprogramm genutzt werden können.  
  
> [!NOTE]
>  Das RegPkg-Tool ist keine weitervertreibbare Komponente verfügbar und kann nicht verwendet werden, um ein VSPackage auf dem System eines Benutzers zu registrieren.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Warum sollten VSPackages nicht während der Installation selbst registrieren  
 Die VSPackage-Installationsprogramme sollten auf Self-Registrierung nicht verlassen. Auf den ersten Blick scheint behalten ein VSPackage Registrierungswerte nur im VSPackage selbst eine gute Idee. Es wird angenommen, dass Entwickler die Registrierungswerte verfügbar für die routinemäßige Arbeit benötigen, und testen, es ist sinnvoll, vermeiden, dass eine separate Kopie der Registrierungsdaten die Installer. Das Installationsprogramm kann für das VSPackage, Schreiben Registrierungseinträge beruhen.  
  
 Beim gut theoretisch weist Self-Registrierung mehrere Fehler, die es für die VSPackage-Installation ungeeignet machen:  
  
-   Ordnungsgemäß unterstützen, Installation, Deinstallation Rollback der Installation und Deinstallation Rollback erfordert, dass Sie vier benutzerdefinierte Aktionen für alle verwalteten VSPackage zu erstellen, das durch Aufrufen von RegPkg selbst registriert.  
  
-   Der Ansatz zur Unterstützung von Seite-an-Seite ist möglicherweise, dass Sie vier benutzerdefinierte Aktionen, das Aufrufen von erstellen "regsvr32" oder RegPkg für jede unterstützte Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Eine Installation mit Self-registrierten Module kann nicht sicher zurückgesetzt werden, da es gibt keine Möglichkeit, der darüber informiert, wenn die Self-registrierten Schlüssel durch eine andere Funktion oder eine Anwendung verwendet werden.  
  
-   Self-registrierten DLLs verknüpft manchmal mit zusätzlichen DLLs, die nicht vorhanden sind oder die Protokolldateiversion passt. Im Gegensatz dazu können Windows Installer DLLs, die bei der Registrierungstabellen mit keine Abhängigkeit von den aktuellen Status des Systems registrieren.  
  
-   Selbstregistrierungscodes kann verweigert werden, Zugriff auf Netzwerkressourcen wie z. B. Typbibliotheken, wenn eine Komponente ist sowohl als ausführen aus Datenquelle angegeben und wird in der Tabelle SelfReg aufgeführt. Dadurch kann die Installation der Komponente während einer administrative Installation fehlschlägt.  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Managed Package-Registrierung](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
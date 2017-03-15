---
title: "VSPackage-Registrierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Registrierung VSPackages"
  - "Registrieren von VSPackages"
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# VSPackage-Registrierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackages müssen informieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dass diese installiert werden und sollte geladen werden. Dieser Vorgang erfolgt durch das Schreiben von Informationen in der Registrierung. Das ist eine normale Auftrag eines Installationsprogramms.  
  
> [!NOTE]
>  Es ist ein allgemein akzeptierten Praxis während der Entwicklung von VSPackages, Self\-Registrierung zu verwenden. Allerdings [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] Partner darf nicht ihre Produkte mithilfe von Self\-Registrierung als Teil der Installation ausgeliefert.  
  
 Registrierungseinträge in einem Windows Installer\-Paket werden in der Regel in der Tabelle der Registrierung vorgenommen. Sie können auch Erweiterungen in der Tabelle Registrierung registrieren. Windows Installer bietet jedoch integrierten Unterstützung durch den Programmbezeichner \(ProgId\), Klasse, Erweiterung und Verb\-Tabellen. Weitere Informationen finden Sie unter [Datenbanktabellen](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Achten Sie darauf, dass die Einträge in der Registrierung der Komponente zugeordnet werden, die für Ihre gewählte Side\-by\-Side\-Strategie geeignet ist. Beispielsweise sollten Einträge in der Registrierung für eine freigegebene Datei dieser Datei Windows Installer\-Komponente zugeordnet werden. Ebenso sollten Registrierungseinträge für eine Datei hängt von der Version der Datei Komponente zugeordnet sein. Andernfalls installieren oder deinstallieren Sie das VSPackage für eine Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] konnte das VSPackage in anderen Versionen unterbrechen. Weitere Informationen finden Sie unter [Unterstützung von mehreren Versionen von Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Die einfachste Möglichkeit zum Verwalten der Registrierung werden dieselben Daten in die gleichen Dateien für die entwicklerregistrierung und Installationszeit Registrierung verwenden. Beispielsweise können einige Installer Development Tools im reg\-Format zur Buildzeit nutzen. Wenn Entwickler reg\-Dateien für ihre eigenen täglichen Entwicklung und Debuggen, dieselben Dateien können im Installationsprogramm automatisch eingeschlossen. Wenn Sie die Registrierungsdaten nicht automatisch freigeben können, müssen Sie sicherstellen, dass das Installationsprogramm Kopie der Registrierungsdaten aktuell sind.  
  
## Nicht verwaltete VSPackages registrieren  
 Nicht verwaltete VSPackages \(einschließlich der von der Visual Studio\-Paketvorlage generierten\) verwenden Sie ATL\-Stil .rgs Dateien zum Speichern von Registrierungsinformationen. Das Dateiformat .rgs bezieht sich auf ATL und nicht in der Regel als genutzt werden – wird durch eine Installation Erstellungstool. Die Registrierungsinformationen für das VSPackage\-Installationsprogramm muss separat verwaltet werden. Beispielsweise können Entwickler Dateien in .reg\-Format mit .rgs Änderungen synchronisiert. Reg\-Dateien mit RegEdit für Entwicklungen zusammengeführt oder durch ein Installationsprogramm genutzt werden.  
  
## Verwaltete VSPackages registrieren  
 Das RegPkg\-Tool liest die Registrierung Attribute aus einem verwalteten VSPackage und können entweder die Informationen direkt in der Registrierung oder Write\-reg\-Format\-Dateien, die durch ein Installationsprogramm genutzt werden können.  
  
> [!NOTE]
>  Das RegPkg\-Tool kann nicht verteilt werden und kann nicht verwendet werden, um ein VSPackage auf dem System eines Benutzers zu registrieren.  
  
## Warum sollten VSPackages nicht zum Zeitpunkt der Installation selbst registrieren  
 Die VSPackage\-Installationsprogramme sollten nicht davon abhängig, selbst registrieren. Auf den ersten Blick scheint ein VSPackage\-Registrierungswerte nur in das VSPackage selbst halten sollten. Entwickler benötigen die Registrierungswerte verfügbar für die routinemäßige Arbeit und testen, ist es sinnvoll, vermeiden, dass eine separate Kopie der Registrierungsdaten im Installationsprogramm. Das Installationsprogramm kann das VSPackage Schreiben von Registrierungswerten abhängig.  
  
 Bei gut in der Theorie ist selbst registrieren verschiedene Mängel, die es für VSPackage\-Installation ungeeignet:  
  
-   Ordnungsgemäß unterstützen, Installation, Deinstallation, Rollback der Installation und Deinstallation Rollback erfordert, dass Sie vier benutzerdefinierte Aktionen für jedes verwaltete VSPackages zu erstellen, die durch Aufrufen von RegPkg selbst registriert.  
  
-   Ihr Ansatz zur Unterstützung von Side\-by\-Side\-möglicherweise, dass Sie vier benutzerdefinierte Aktionen erstellen, das Aufrufen von RegSvr32 oder RegPkg für jede unterstützte Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Eine Installation mit sich selbst registrierten Module kann nicht sicher zurückgesetzt werden, da es gibt keine Möglichkeit der mitgeteilt wird, ob der automatisch registriert Schlüssel durch eine andere Funktion oder eine Anwendung verwendet werden.  
  
-   Automatisch registriert DLLs verknüpft gelegentlich auf zusätzliche DLLs, die nicht vorhanden sind oder die falsche Version. Im Gegensatz dazu können Windows Installer keine Abhängigkeit von den aktuellen Zustand des Systems den Registrierungstabellen mit DLLs registrieren.  
  
-   Selbstregistrierungscodes kann verweigert werden, Zugriff auf Netzwerkressourcen, z. B. Typbibliotheken, wenn eine Komponente ist sowohl als angegeben Run\-from\-Source\- und finden Sie in der Tabelle SelfReg. Dadurch kann die Installation der Komponente während einer administrativen Installation fehlschlägt.  
  
## Siehe auch  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Managed Package Registration](http://msdn.microsoft.com/de-de/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
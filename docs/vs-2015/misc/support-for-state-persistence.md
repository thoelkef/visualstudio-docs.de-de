---
title: Unterstützung der Zustands Persistenz | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434318"
---
# <a name="support-for-state-persistence"></a>Unterstützung von Statuspersistenz
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kann den Status von gemeinsamen Objekten beibehalten. Beispielsweise werden Projektmappen-und Projekteigenschaften in Projektmappen-und Projektdateien gespeichert und wieder hergestellt. Benutzereinstellungen können in Einstellungsdateien exportiert und aus Ihnen importiert werden.  
  
 VSPackages basieren in der Regel auf lokalem Speicher, entweder in der Systemregistrierung oder im Ordner "Anwendungsdaten" für den aktuellen Benutzer oder Computer. Werte, die einen geringen Speicherplatz benötigen, z. b. ganze Zahlen und Zeichen folgen, werden in der Regel in der Systemregistrierung gespeichert. Werte, die viel Speicherplatz benötigen, z. b. Bitmaps, werden in einer Datei gespeichert. Der Pfad der Datei kann selbst in der Systemregistrierung gespeichert werden. Der Persistenzmechanismus muss über die Berechtigung für den Zugriff auf den lokalen Speicher verfügen.  
  
## <a name="support-for-locating-local-storage"></a>Unterstützung für lokale Speicherung  
 Die- <xref:Microsoft.VisualStudio.Shell.Package> Klasse unterstützt das Suchen von Zustandsinformationen im Ordnersystem Registrierung oder Anwendungsdaten für den aktuellen Benutzer oder Computer.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Gibt den Pfad des Registrierungs Stamms des lokalen Computers für zurück [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , z. b. HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp.  
  
 Der lokale Registrierungs Stamm wird vom Dienst abgerufen <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> . Wenn dies nicht verfügbar ist, wird es aus dem- <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> Attribut des VSPackage abgerufen.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Gibt den Pfad des Registrierungs Stamms (pro Computer) des aktuellen Benutzers für zurück [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , z. b. HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp.  
  
 Der lokale Registrierungs Stamm wird vom Dienst abgerufen <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> . Wenn dies nicht verfügbar ist, wird es aus dem defaultlocalregistryroot-Attribut des VSPackage abgerufen.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Gibt den Pfad des Verzeichnisses zurück, das als gemeinsames Repository für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Daten für den aktuellen Roamingbenutzer fungiert, z. b. c:\Documents und Settings \\ *youraccountname*\Application data\microsoft\visualstudio\8.0exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Gibt den Pfad des Verzeichnisses zurück, das als gemeinsames Repository für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Daten für den aktuellen nicht Roamingbenutzer fungiert, z. b. c:\Documents und Settings \\ *youraccountname*\Local Settings\Application data\microsoft\visualstudio\8.0exp.  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPackage-Status](../misc/vspackage-state.md)
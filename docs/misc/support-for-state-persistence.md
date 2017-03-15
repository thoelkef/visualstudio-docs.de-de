---
title: "Unterst&#252;tzung von Statuspersistenz | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Statuspersistenz, Unterstützung von MPF (Managed Package Framework)"
  - "Managed Package Framework (MPF), Unterstützung von Statuspersistenz"
  - "Status, Persistenz"
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# Unterst&#252;tzung von Statuspersistenz
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kann den Zustand von allgemeinen Objekten beibehalten.  Beispielsweise werden Projektmappe und zu Projekteigenschaften gespeichert und wiederhergestellt aus der Projektmappe und die Projektdateien.  Benutzereinstellungen können von Einstellungsdateien exportiert und importiert werden.  
  
 VSPackages erfordern in der Regel auf dem lokalen Speicher entweder in der Systemregistrierung oder im datenordner Anwendung für den aktuellen Benutzer oder Computer.  Werte, die eine kleine Menge an Speicherplatz für Speicher, z. B. ganze Zahlen und Zeichenfolgen erfordern, werden in der Regel in der Systemregistrierung gespeichert.  Werte, die viele Platz zum Speichern, z. B. Bitmaps werden müssen, werden in einer Datei gespeichert.  Der Dateipfad kann auch in der Systemregistrierung gespeichert werden.  Der Mechanismus zur Persistenz muss über die Berechtigung, den lokalen Speicher zuzugreifen.  
  
## Unterstützung zum Suchen des lokalen Speicher  
 Die <xref:Microsoft.VisualStudio.Shell.Package>\-Klasse bietet Unterstützung zum Suchen von Zustandsinformationen in der Systemregistrierung oder im datenordner Anwendung für den aktuellen Benutzer oder den Computer.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Gibt den Pfad des stamms Registrierung des lokalen Computers für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]z. B. HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ 8.0Exp zurück.  
  
 Der lokale Registrierungsstamm wird vom <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> Dienst abgerufen.  Wenn dies nicht möglich ist, wird es vom <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> VSPackages Attribut abzurufen.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Gibt den Pfad des aktuellen stamms Registrierung des Benutzers \(pro Computer\) für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]z. B. HKEY\_CURRENT\_USER \\ Software \\ Microsoft \\ VisualStudio \\ 8.0Exp zurück.  
  
 Der lokale Registrierungsstamm wird vom <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> Dienst abgerufen.  Wenn dies nicht möglich ist, wird es vom DefaultLocalRegistryRoot\-Attribut VSPackages erhalten.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Gibt den Pfad des Verzeichnisses zurück, das als allgemeines Repository für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Daten für den aktuellen Benutzer Roaming, z. B. C:\\Documents and Settings\\*TheAccountName*\\ Anwendungsdaten \\ Microsoft \\ VisualStudio \\ 8.0Exp dient.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Gibt den Pfad des Verzeichnisses zurück, das als allgemeines Repository für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Daten für den aktuellen Benutzer, der kein Roaming verwendet, z. B. C:\\Documents and Settings\\*TheAccountName*\\ Lokale Einstellungen \\ Anwendungsdaten \\ Microsoft \\ VisualStudio \\ 8.0Exp dient.  
  
## Siehe auch  
 [VSPackage\-Status](../misc/vspackage-state.md)
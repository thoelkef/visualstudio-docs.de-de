---
title: "Devenv-Befehlszeilenschalter f&#252;r VSPackage-Entwicklung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/ Setup-Befehlszeilenoption"
  - "/ resetskippkgs-Befehlszeilenschalter"
  - "Befehlszeilenschalter NoVSIP"
  - "die Befehlszeilenoption/rootsuffix"
  - "Befehlszeilenschalter"
  - "Visual Studio SDK-Registrierung"
  - "Switches-Befehlszeile"
  - "Visual Studio-SDK, Befehlszeilenoptionen"
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Devenv-Befehlszeilenschalter f&#252;r VSPackage-Entwicklung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ermöglicht Entwicklern das Automatisieren von Aufgaben in der Befehlszeile beim Ausführen von devenv.exe, die Datei, die die integrierte Entwicklungsumgebung \(IDE\) von Visual Studio wird gestartet.  
  
 Es gibt u. a. folgende Aufgaben:  
  
-   Bereitstellen von Anwendungen in vordefinierten Konfigurationen von außerhalb der IDE.  
  
-   Erstellen von Projekten, die mit der Voreinstellung wird automatisch Buildeinstellungen oder Debugkonfigurationen.  
  
-   Laden die IDE in bestimmten Konfigurationen von außerhalb der IDE. Darüber hinaus können Sie die IDE beim Start anpassen.  
  
## Richtlinien für Switches  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Dokumentation beschreibt die Benutzerebene Devenv\-Befehlszeilenschalter. Weitere Informationen finden Sie unter [Devenv\-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md). Devenv unterstützt auch zusätzliche Befehlszeilenoptionen, die mit der VSPackage\-Entwicklung, Bereitstellung und Debuggen nützlich sind.  
  
|Befehlszeilenoption|Beschreibung|  
|-------------------------|------------------|  
|\/ SafeMode|Startet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus geladen wird, nur die Standard\-IDE und Dienste. Der\/SafeMode\-Schalter wird verhindert, dass alle Drittanbieter\-VSPackages lädt beim [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gestartet wird, um stabile Ausführung sicherzustellen.<br /><br /> Dieser Schalter akzeptiert keine Argumente.|  
|\/ resetskippkgs|Löscht alle Optionen für das Laden, die von Benutzern hinzugefügt wurden, die Laden von problematischen VSPackages verhindern möchten überspringen startet dann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Das Vorhandensein eines SkipLoading\-Tags wird das Laden von VSPackages deaktiviert. Das Laden von VSPackages deaktivieren das Tag erneut aktiviert werden.<br /><br /> Dieser Schalter akzeptiert keine Argumente.|  
|\/ rootsuffix|Startet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mit einem anderen Speicherort. Der folgende Befehl ausgeführt wird, durch die Verknüpfung erstellt, indem die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Installer:<br /><br /> Devenv\/rootsuffix exp<br /><br /> In diesem Fall gibt exp einen Speicherort mit einem bestimmten Suffix, z. B. 10.0Exp statt 10.0. Die experimentelle Instanz können Sie ein VSPackage separat von der Instanz Debuggen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Verwendung von Code schreiben.<br /><br /> Diese Option kann eine beliebige Zeichenfolge nehmen, die einen Ort, den Sie erstellt haben identifiziert, mithilfe von VSRegEx.exe. Weitere Informationen finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).|  
|\/Splash|Zeigt die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Begrüßungsbildschirm wie gewohnt, und zeigt anschließend ein Meldungsfeld vor dem Anzeigen der Haupt\-IDE. Das Meldungsfeld können Sie die Untersuchen des Begrüßungsbildschirm, z. B. für ein VSPackage\-Produktsymbol überprüfen.<br /><br /> Dieser Schalter akzeptiert keine Argumente.|  
  
## Siehe auch  
 [Hinzufügen von Befehlszeilenoptionen](../extensibility/adding-command-line-switches.md)   
 [Devenv\-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)
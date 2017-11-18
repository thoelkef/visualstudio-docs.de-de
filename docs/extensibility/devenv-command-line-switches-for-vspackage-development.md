---
title: "Devenv-Befehlszeilenschalter für die VSPackage-Entwicklung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /setup command line switch
- /resetskippkgs command line switch
- /noVSIP command line switch
- /rootsuffix command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca93d63236eb1b50663eff4c86a6ae3603600802
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Devenv-Befehlszeilenschalter für die VSPackage-Entwicklung
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ermöglicht Entwicklern das Automatisieren von Tasks über die Befehlszeile beim devenv.exe, die Datei ausführen, die die integrierte Entwicklungsumgebung (IDE) von Visual Studio wird gestartet.  
  
 U. a. folgende Aufgaben:  
  
-   Bereitstellen von Anwendungen in vordefinierten Konfigurationen von außerhalb der IDE.  
  
-   Automatisches Erstellen von Projekten mithilfe der vorab festgelegten Buildeinstellungen oder Debugkonfigurationen.  
  
-   Beim Laden der IDE in bestimmten Konfigurationen von außerhalb der IDE. Darüber hinaus können Sie die IDE beim Start anpassen.  
  
## <a name="guidelines-for-switches"></a>Richtlinien für Switches  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Dokumentation beschreibt die Benutzerebene Devenv-Befehlszeilenschalter. Weitere Informationen finden Sie unter [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md). Devenv unterstützt auch zusätzliche Befehlszeilenoptionen, die mit der VSPackage-Entwicklung, Bereitstellung und Debuggen nützlich sind.  
  
|Befehlszeilenschalter|Beschreibung|  
|--------------------------|-----------------|  
|/ SafeMode|Startet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus zu laden, nur die Standard-IDE und Dienste. Der/SafeMode-Schalter wird verhindert, dass es sich bei allen eines Drittanbieters VSPackages vor dem Laden, wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gestartet wird, wodurch sichergestellt wird stabile Ausführung.<br /><br /> Der Schalter verwendet keine Argumente.|  
|/ resetskippkgs|Löscht alle Optionen für das Laden, die von Benutzern hinzugefügt wurden, die auf das Laden von problematischen VSPackages verhindern möchten überspringen startet dann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Das Vorhandensein eines SkipLoading-Tags wird das Laden eines VSPackage deaktiviert. Das Laden des VSPackage deaktivieren das Tag wieder aktiviert werden.<br /><br /> Der Schalter verwendet keine Argumente.|  
|/rootsuffix|Startet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mit einem anderen Speicherort. Der folgende Befehl ausgeführt wird, durch die Verknüpfung erstellt, indem die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Installer:<br /><br /> Devenv /RootSuffix exp<br /><br /> Exp bezeichnet in diesem Fall einen Speicherort mit einem bestimmten Suffix, z. B. 10.0Exp statt 10.0. Die experimentelle Instanz können Sie eine VSPackage separat von der Instanz von Debuggen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , dass Sie verwenden, um Code zu schreiben.<br /><br /> Dieser Schalter dauert eine beliebige Zeichenfolge, die einen Ort identifiziert, den Sie mithilfe von VSRegEx.exe erstellt haben. Weitere Informationen finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).|  
|/Splash|Zeigt die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] splash-Bildschirm wie gewohnt aus, und klicken Sie dann vor dem Anzeigen der Haupt-IDE wird ein Meldungsfeld. Das Meldungsfeld können Sie die zu untersuchen, das den Begrüßungsbildschirm, z. B. für ein VSPackage-Produkt-Symbol zu überprüfen.<br /><br /> Der Schalter verwendet keine Argumente.|  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Befehlszeilenoptionen](../extensibility/adding-command-line-switches.md)   
 [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)
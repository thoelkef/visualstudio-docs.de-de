---
title: Debug-Befehls Zeilenschalter für die VSPackage-Entwicklung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
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
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97ce429a7140d7b95393c2dcb8b34491b3adfefa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185276"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Devenv-Befehlszeilenschalter für die VSPackage-Entwicklung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ermöglicht Entwicklern das Automatisieren von Aufgaben über die Befehlszeile, wenn devenv.exe ausgeführt wird, die Datei, die die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio startet.  
  
 Zu den Tasks gehören:  
  
- Bereitstellen von Anwendungen in vorgefertigten Konfigurationen von außerhalb der IDE.  
  
- Automatisches Erstellen von Projekten mithilfe vordefinierter Buildeinstellungen oder Debugkonfigurationen.  
  
- Laden der IDE in bestimmten Konfigurationen, von außerhalb der IDE. Außerdem können Sie die IDE beim Start anpassen.  
  
## <a name="guidelines-for-switches"></a>Richtlinien für Switches  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in der Dokumentation werden die Befehls Zeilenschalter auf Benutzerebene beschrieben. Weitere Informationen finden Sie unter [devenv-Befehls Zeilenschalter](../ide/reference/devenv-command-line-switches.md). Devenv unterstützt auch zusätzliche Befehls Zeilenschalter, die für die Entwicklung, Bereitstellung und das Debuggen von VSPackages nützlich sind.  
  
|Befehls Zeilenschalter|Beschreibung|  
|--------------------------|-----------------|  
|/safemode|Gestartet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] im abgesicherten Modus und lädt nur die Standard-IDE und-Dienste. Der/safemode-Schalter verhindert, dass alle VSPackages von Drittanbietern geladen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] werden, wenn gestartet wird, wodurch eine stabile Ausführung sichergestellt wird.<br /><br /> Der Schalter verwendet keine Argumente.|  
|/resetskippkgs|Löscht alle Skip-Lade Optionen, die von Benutzern hinzugefügt wurden, die das Laden von problematischen VSPackages vermeiden möchten, und startet dann [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Das vorhanden sein eines SkipLoading-Tags deaktiviert das Laden eines VSPackages. Wenn Sie das Tag löschen, wird das Laden des VSPackage erneut aktiviert.<br /><br /> Der Schalter verwendet keine Argumente.|  
|/rootsuffix|Startet mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] einem alternativen Speicherort. Der folgende Befehl wird von der Verknüpfung ausgeführt, die vom Installationsprogramm erstellt wurde [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] :<br /><br /> Debug-/RootSuffix-Exp<br /><br /> In diesem Fall identifiziert Exp einen Speicherort mit einem bestimmten Suffix, z. b. 10.0 Exp anstelle von 10,0. Die experimentelle Instanz ermöglicht Ihnen, ein VSPackage getrennt von der-Instanz zu Debuggen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , die Sie zum Schreiben von Code verwenden.<br /><br /> Dieser Switch kann jede beliebige Zeichenfolge verwenden, die einen Speicherort identifiziert, den Sie mit VSRegEx.exe erstellt haben. Weitere Informationen finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md).|  
|/splash|Zeigt den Begrüßungs [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bildschirm wie gewohnt an und zeigt ein Meldungs Feld an, bevor die Haupt-IDE angezeigt wird. Mit dem Meldungs Feld können Sie den Begrüßungsbildschirm untersuchen, um z. b. nach einem VSPackage-Produktsymbol zu suchen.<br /><br /> Der Schalter verwendet keine Argumente.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Befehls zeilenschaltern](../extensibility/adding-command-line-switches.md)   
 [Debug-Befehls Zeilenschalter](../ide/reference/devenv-command-line-switches.md)

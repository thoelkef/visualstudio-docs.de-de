---
title: Devenv-Befehlszeilenschalter für die Entwicklung von VSPackage | Microsoft-Dokumentation
ms.date: 11/04/2016
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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4333f7e0c892771ffb9b4643f4814cf3352a8f1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820292"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>Devenv-Befehlszeilenschalter für die Entwicklung von VSPackages
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ermöglicht es Entwicklern, Aufgaben, die über die Befehlszeile zu automatisieren, Ausführung *devenv.exe*, die Datei, die die integrierte Entwicklungsumgebung (IDE) von Visual Studio wird gestartet.  

 Tasks gehört Folgendes:  

-   Bereitstellen von Anwendungen in vordefinierten Konfigurationen von außerhalb der IDE aus.  

-   Erstellen von Projekten mit der Voreinstellung wird automatisch Buildeinstellungen oder Debugkonfigurationen.  

-   Laden die IDE in spezifischen Konfigurationen außerhalb der IDE aus. Darüber hinaus können Sie die IDE beim Start anpassen.  

## <a name="guidelines-for-switches"></a>Richtlinien für switches  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Dokumentation wird beschrieben, die auf Benutzerebene Devenv-Befehlszeilenschalter. Weitere Informationen finden Sie unter [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md). Devenv unterstützt auch zusätzliche Befehlszeilenoptionen, die mit der VSPackage-Entwicklung, Bereitstellung und Debuggen hilfreich sind.  


| Befehlszeilenschalter | Beschreibung |
|---------------------| - |
| SafeMode | Startet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im abgesicherten Modus geladen werden, nur die Standard-IDE und Dienste. Der SafeMode-Schalter wird verhindert, dass es sich bei allen VSPackages von Drittanbietern geladen, wenn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gestartet wird, damit die stabile Ausführung sicher.<br /><br /> Der Schalter verwendet keine Argumente. |
| / resetskippkgs | Löscht alle Optionen für das Laden, die von Benutzern, die möchten hinzugefügt wurden, vermeiden des Ladens von problematischen VSPackages, überspringen Sie startet dann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Das Vorhandensein eines SkipLoading-Tags deaktiviert das Laden eines VSPackage. Das Löschen des Tags das Laden des VSPackage erneut aktiviert werden.<br /><br /> Der Schalter verwendet keine Argumente. |
| / rootsuffix | Startet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mit einem alternativen Speicherort. Der folgende Befehl ausgeführt wird, durch die Verknüpfung erstellt werden, indem die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Installer:<br /><br /> Devenv/rootsuffix exp<br /><br /> In diesem Fall gibt "exp" einen Speicherort mit einem bestimmten Suffix, z. B. 10.0Exp statt 10.0. Die experimentelle Instanz können Sie eine VSPackage separat von der Instanz von Debuggen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , dass Sie verwenden, um Code zu schreiben.<br /><br /> Dieser Schalter dauert eine beliebige Zeichenfolge, die einen Speicherort angibt, den Sie mithilfe von VSRegEx.exe erstellt haben. Weitere Informationen finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md). |
| /Splash | Zeigt die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Begrüßungsbildschirm wie üblich, und klicken Sie dann zeigt ein Meldungsfeld vor dem Anzeigen der Haupt-IDE. Das Meldungsfeld können Sie den Begrüßungsbildschirm, zu prüfen, ein Symbol für den VSPackage-Produkt, z. B. zu untersuchen.<br /><br /> Der Schalter verwendet keine Argumente. |

## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Befehlszeilenschaltern](../extensibility/adding-command-line-switches.md)   
 [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)
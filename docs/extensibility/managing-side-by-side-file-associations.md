---
title: Verwalten von Seite-an-Seite Dateizuordnungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d0a6f8ec88a49b785b771aef51dc25b5646ffda
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="managing-side-by-side-file-associations"></a>Seite-an-Seite Dateizuordnungen verwalten
Wenn Ihr VSPackage dateizuordnungen bereitstellt, müssen Sie entscheiden, Behandeln von Seite-an-Seite-Installationen in der eine bestimmte Version [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aufgerufen werden soll, um eine Datei zu öffnen. Nicht kompatiblen Dateiformate zusammengesetzte das Problem.  
  
 Benutzer erwarten, dass eine neue Version eines Produkts, die mit früheren Versionen kompatibel sein, damit vorhandene Dateien in einer neuen Version geladen werden können, ohne dass Daten verloren gehen. Im Idealfall kann Ihr VSPackage zu laden und die Dateiformate früherer Versionen zu speichern. Wenn dies nicht "true" ist, sollten Sie so aktualisieren Sie das Dateiformat auf die neue Version Ihres VSPackage anbieten. Der Nachteil dieses Ansatzes ist, dass die aktualisierte Datei in der früheren Version geöffnet werden kann.  
  
 Um dieses Problem zu vermeiden, können Sie Erweiterungen ändern, sobald Dateiformate nicht kompatibel sind. Beispielsweise, Version 1 von Ihr VSPackage verwenden die Erweiterung, .mypkg10 und Version 2 können die Erweiterung .mypkg20. Dieser Unterschied identifiziert das VSPackage, das eine bestimmte Datei geöffnet wird. Wenn Sie die Liste der Programme, die mit der alten Erweiterung einhergehen neuere VSPackages hinzugefügt haben, können Benutzer mit der rechten Maustaste in der das und auswählen, um es in einem neueren VSPackage zu öffnen. An diesem Punkt kann Ihr VSPackage bieten, aktualisieren die Datei in das neue Format, oder öffnen Sie die Datei, und Verwalten der Kompatibilität mit früheren Versionen des VSPackage.  
  
> [!NOTE]
>  Sie können diese Vorgehensweisen kombinieren. Sie können z. B. bieten Abwärtskompatibilität durch eine ältere Datei laden und das Dateiformat aktualisieren, wenn der Benutzer es speichert bieten.  
  
## <a name="facing-the-problem"></a>Mit Internetzugriff des Problems  
 Wenn Sie mehrere VSPackages von Seite-an-Seite auf die gleiche Erweiterung verwenden möchten, müssen Sie auswählen, die Version des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , die mit der Erweiterung verknüpft ist. Hier sind zwei Alternativen:  
  
-   Öffnen Sie die Datei in der neuesten Version des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auf dem Computer eines Benutzers installiert.  
  
     Bei dieser Vorgehensweise wird das Installationsprogramm zuständig für das Ermitteln der neuesten Version der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und einbeziehen, die in den Registrierungseintrag für die dateizuordnung geschrieben. In einer Windows Installer-Paket können Sie benutzerdefinierte Aktionen zum Festlegen einer Eigenschaft, die die neueste Version von einschließen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    > [!NOTE]
    >  In diesem Kontext bedeutet "Letzter" "neueste unterstützte Version." Diese Installer-Einträge erkennt nicht automatisch einen nachfolgenden Freigaben der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Einträge im [Ermitteln von Systemanforderungen](../extensibility/internals/detecting-system-requirements.md) und [Befehle, muss sein führen Sie nach der Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md) ähneln den Vorgängen, die hier vorgestellten und sind erforderlich, um zusätzliche Versionen eines unterstützen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Die folgenden Zeilen in der Tabelle CustomAction legen Sie die DEVENV_EXE_LATEST-Eigenschaft auf eine Eigenschaft festlegen, indem die AppSearch sein und RegLocator Tabellen im [Befehle, muss sein führen Sie nach der Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md). Zeilen in der Tabelle InstallExecuteSequence planen Sie die benutzerdefinierten Aktionen früh in der Execute-Sequenz. Die Werte in der Bedingung Spalte festlegen, dass die Logik:  
  
    -   Visual Studio .NET 2002 ist die neueste Version ist nur vorhanden, Version.  
  
    -   Visual Studio .NET 2003 ist die neueste Version nur, wenn es vorhanden ist und [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist nicht vorhanden.  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]die neueste Version ist, wird jedoch nur vorhanden, Version.  
  
     Das Ergebnis ist, dass DEVENV_EXE_LATEST den Pfad der neuesten Version von devenv.exe enthält.  
  
    ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>CustomAction Tabellenzeilen, die bestimmen, die neueste Version von Visual Studio  
  
    |Aktion|Typ|Quelle|Ziel|  
    |------------|----------|------------|------------|  
    |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
    |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
    |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
    ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>InstallExecuteSequence Tabellenzeilen, die bestimmen, die neueste Version von Visual Studio  
  
    |Aktion|Bedingung|Sequenz|  
    |------------|---------------|--------------|  
    |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 UND NICHT (DEVENV_EXE_2003 ODER DEVENV_EXE_2005)|410|  
    |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 UND NICHT DEVENV_EXE_2005|420|  
    |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
     Sie können die DEVENV_EXE_LATEST-Eigenschaft in der Tabelle der Registrierung von Windows Installer-Paket verwenden, Schreiben Sie den HKEY_CLASSES_ROOT*ProgId*Standardwert des Schlüssels ShellOpenCommand [DEVENV_EXE_LATEST] "%1"  
  
-   Führen Sie einen freigegebenen Startprogramms, die die beste Wahl aus VSPackage-Versionen verfügbar machen kann.  
  
     Der Entwickler von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] diese Weise behandeln die komplexe Anforderungen, der mehrere Formate von Projektmappen und Projekten, die aus vielen Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Bei dieser Vorgehensweise registrieren Sie ein Programm Startprogramm als anwendungserweiterungs-Handler. Das Startprogramm untersucht die Datei, und entscheidet, welche Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und diese Datei können Sie Ihr VSPackage behandeln. Z. B. wenn ein Benutzer eine Datei, die von einer bestimmten Version Ihres VSPackage zuletzt gespeichert wurde öffnet, das Startprogramm kann starten, VSPackage in der entsprechenden Version der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Darüber hinaus konnte ein Benutzer das Startprogramm um immer die neueste Version Starten konfiguriert werden. Ein Startprogramm kann auch einen Benutzer so aktualisieren Sie das Format der Datei aufgefordert werden. Wenn das Format der Datei eine Versionsnummer enthält, könnte das Startprogramm einen Benutzer informieren, ist, die als eine oder mehrere der installierten VSPackages höher ist das Dateiformat von einer Version.  
  
     Das Startprogramm sollte in einer Windows Installer-Komponente, die mit allen Versionen von Ihr VSPackage gemeinsam verwendet wird. Dieser Prozess stellt sicher, dass die neueste Version immer installiert ist und wird nicht entfernt werden, bis alle Versionen Ihres VSPackage deinstalliert werden. Auf diese Weise werden dateizuordnungen und andere Registrierungseinträge der startprogrammkomponente beibehalten, auch wenn eine Version des VSPackage deinstalliert wird.  
  
## <a name="uninstall-and-file-associations"></a>Deinstallieren und Dateizuordnungen  
 Deinstallieren eine VSPackage, die Registrierungseinträge für dateizuordnungen schreibt entfernt dateizuordnungen. Deshalb hat die Erweiterung keine zugeordneten Programme. Windows Installer ist nicht "die Registrierungseinträge, die hinzugefügt wurden, bei der Installation des VSPackages recover". Es gibt folgende Möglichkeiten, dateizuordnungen eines Benutzers zu beheben:  
  
-   Verwenden Sie einen freigegebenen startprogrammkomponente wie oben beschrieben.  
  
-   Weisen Sie den Benutzer, eine Reparatur der Version des VSPackage auszuführen, die der Benutzer möchte die dateizuordnung besitzen.  
  
-   Geben Sie ein separates ausführbares Programm, das die entsprechenden Registrierungseinträge ändert.  
  
-   Geben Sie eine Konfiguration Optionen oder im aktiven Dialogfeld, mit dem Benutzer dateizuordnungen auswählen und Freigeben von Zuordnungen verloren gehen. Weisen Sie die Benutzer nach der Deinstallation ausgeführt.  
  
## <a name="see-also"></a>Siehe auch  
 [Registrieren Dateierweiterungen für Seite-an-Seite-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Registrieren von Verben für Dateierweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)
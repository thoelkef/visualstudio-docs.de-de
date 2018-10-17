---
title: Verwalten von Seite-an-Seite Dateizuordnungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55a3649385ca8fc840bed8bd28555bcb17f6ac91
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253980"
---
# <a name="managing-side-by-side-file-associations"></a>Verwalten von parallelen Dateizuordnungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn das VSPackage dateizuordnungen bereitstellt, müssen Sie entscheiden, das Durchführen von Seite-an-Seite-Installationen, in denen eine bestimmte Version [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zum Öffnen einer Datei aufgerufen werden soll. Nicht kompatiblen Dateiformate zusammengesetzte das Problem.  
  
 Benutzer erwarten, dass eine neue Version eines Produkts, die mit früheren Versionen kompatibel sein, damit vorhandene Dateien in einer neuen Version geladen werden können, ohne dass Daten verloren gehen. Im Idealfall kann Ihr VSPackage sowohl laden und speichern die Dateiformate von früheren Versionen haben. Wenn dies nicht "true" ist, sollte Sie bieten das Dateiformat auf die neue Version Ihres VSPackage zu aktualisieren. Der Nachteil dieses Ansatzes ist, dass die aktualisierte Datei in der früheren Version geöffnet werden kann.  
  
 Um dieses Problem zu vermeiden, können Sie Erweiterungen ändern, wenn Dateiformate nicht kompatibel sind. Version 1 Ihres VSPackage kann z. B. verwenden, die Erweiterung, .mypkg10 und Version 2 können die Erweiterung .mypkg20. Dieser Unterschied identifiziert das VSPackage, das eine bestimmte Datei geöffnet wird. Wenn Sie neuere VSPackages zur Liste der Programme, die mit der alten Erweiterung zugeordnet sind hinzufügen, können Benutzer mit der rechten Maustaste in der das und auswählen, um es in einem neueren VSPackage zu öffnen. An diesem Punkt kann Ihr VSPackage bieten, aktualisieren die Datei in das neue Format, oder öffnen Sie die Datei, und Verwalten der Kompatibilität mit früheren Versionen des VSPackage.  
  
> [!NOTE]
>  Sie können diese Ansätze kombinieren. Sie können z. B. Abwärtskompatibilität bieten, indem Sie eine ältere Datei laden und das Dateiformat aktualisieren, wenn der Benutzer es speichert bieten.  
  
## <a name="facing-the-problem"></a>Das Problem konfrontiert  
 Wenn Sie mehrere Seite-an-Seite von VSPackages zu derselben Erweiterung verwenden möchten, müssen Sie wählen, dass die Version der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , die Erweiterung zugeordnet ist. Hier sind zwei Möglichkeiten:  
  
-   Öffnen Sie die Datei in der neuesten Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] auf dem Computer eines Benutzers installiert.  
  
     Bei diesem Ansatz ist das Installationsprogramm bestimmen muss, die neueste Version des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] einschließlich, die im Registrierungseintrag für die dateizuordnung geschrieben wurden. In einer Windows Installer-Paket, können Sie benutzerdefinierte Aktionen zum Festlegen einer Eigenschaft, der die neueste Version des angibt einschließen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
    > [!NOTE]
    >  In diesem Kontext bedeutet "latest" "neueste unterstützte Version." Diese Einträge Installationsprogramm erkennt nicht automatisch eine späteren Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Einträge im [Systemanforderungen erkennen](../extensibility/internals/detecting-system-requirements.md) und [Befehle, muss sein führen Sie nach der Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md) ähneln den Vorgängen, die hier vorgestellten und sind erforderlich, um zusätzliche Versionen unterstützen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Die folgenden Zeilen in der Tabelle CustomAction DEVENV_EXE_LATEST Eigenschaft eine Eigenschaft, die von der AppSearch festgelegt ist und RegLocator Tabellen, die in beschriebenen [Befehle, muss sein führen Sie nach der Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md). Zeilen in der Tabelle InstallExecuteSequence planen Sie die benutzerdefinierten Aktionen in einem frühen Zeitpunkt in der Execute-Sequenz. Die Werte in der Bedingung Spalte festlegen, dass die Logik:  
  
    -   Visual Studio .NET 2002 ist die neueste Version aus, wenn es die Version ist nur vorhanden ist.  
  
    -   Visual Studio .NET 2003 ist die neueste Version aus, nur dann, wenn es vorhanden ist und [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ist nicht vorhanden.  
  
    -   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ist die neueste Version aus, wenn es die Version ist nur vorhanden ist.  
  
     Das Ergebnis ist, dass DEVENV_EXE_LATEST den Pfad der neuesten Version von devenv.exe enthält.  
  
    ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>CustomAction Tabellenzeilen, die bestimmen, die neueste Version von Visual Studio  
  
    |Aktion|Typ|Source|Target|  
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
  
     Sie können die DEVENV_EXE_LATEST-Eigenschaft in der Tabelle der Registrierung des Windows Installer-Pakets die HKEY_CLASSES_ROOT schreiben*ProgId*Standardwert des Schlüssels ShellOpenCommand [DEVENV_EXE_LATEST] "%1"  
  
-   Führen Sie einen gemeinsam genutzten Anwendungsstarter-Programm, das die beste Wahl von VSPackage-Versionen zur Verfügung stellen kann.  
  
     Die Entwickler von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dieser Ansatz behandelt die komplexen Anforderungen der mehrere Formate von Projektmappen und Projekte, die aus vielen Versionen der ausgewählten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bei diesem Ansatz registrieren Sie ein Startprogramm-Programm als den Erweiterungs-Handler. Das Startprogramm untersucht die Datei, und entscheidet, welche Version der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und das VSPackage, bestimmte Datei verarbeiten kann. Beispielsweise wenn ein Benutzer eine Datei, die von einer bestimmten Version Ihres VSPackage zuletzt gespeichert wurde öffnet, das Startprogramm kann beginnen, VSPackage in der entsprechenden Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Darüber hinaus kann Benutzer das Startprogramm aus, um immer die neueste Version Starten konfigurieren. Ein Startprogramm kann auch ein Benutzer so aktualisieren das Format der Datei aufgefordert. Wenn das Format der Datei eine Versionsnummer enthält, könnte das Startprogramm für einen Benutzer informieren, wenn das Dateiformat von einer Version ist, die älter als eine oder mehrere der installierten VSPackages.  
  
     Das Startprogramm sollten in einer Windows Installer-Komponente, die mit allen Versionen von einem VSPackage verwendet wird. Dieser Prozess wird sichergestellt, dass die neueste Version immer installiert ist und wird nicht entfernt werden, bis Sie alle Versionen Ihres VSPackage deinstalliert werden. Auf diese Weise werden die "dateizuordnungen" und "andere Registrierungseinträge der startprogrammkomponente beibehalten, auch wenn eine Version des VSPackage deinstalliert wird.  
  
## <a name="uninstall-and-file-associations"></a>Deinstallieren und Dateizuordnungen  
 Deinstallieren eines VSPackage, die Registrierungseinträge für dateizuordnungen schreibt, wird die dateizuordnungen entfernt. Aus diesem Grund hat die Erweiterung keine zugehörigen Programme. Windows Installer ist nicht "die Registrierungseinträge, die hinzugefügt wurden, bei der Installation des VSPackages recover". Hier sind einige Möglichkeiten, um dateizuordnungen eines Benutzers zu beheben:  
  
-   Verwenden Sie eine freigegebene startprogrammkomponente, die wie oben beschrieben.  
  
-   Weisen Sie den Benutzer, eine Reparatur der Version des VSPackage auszuführen, die der Benutzer möchte die dateizuordnung zu besitzen.  
  
-   Geben Sie ein separates ausführbares Programm, das die entsprechenden Registrierungseinträge ändert.  
  
-   Geben Sie eine Konfiguration-Optionen oder im aktiven Dialogfeld, mit dem Benutzer, wählen Sie die dateizuordnungen und Freigeben von verlorenen Zuordnungen. Weisen Sie Benutzer für die Ausführung nach der Deinstallation.  
  
## <a name="see-also"></a>Siehe auch  
 [Registrieren von Dateierweiterungen für Seite-an-Seite-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Registrieren von Verben für Dateierweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)


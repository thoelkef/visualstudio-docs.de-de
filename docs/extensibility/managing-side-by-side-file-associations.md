---
title: "Verwalten von Dateizuordnungen Side-by-Side | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Festlegen von standardmäßigen-Verben"
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Verwalten von Dateizuordnungen Side-by-Side
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn ein VSPackage Dateizuordnungen enthält, müssen Sie entscheiden, wie parallele Installationen behandelt, bei denen eine bestimmte Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aufgerufen werden soll, um eine Datei zu öffnen.  Nicht kompatibler Dateiformate versetzen das Problem zusammen.  
  
 Benutzer eine neue Version eines Produkts, um mit früheren Versionen kompatibel ist, für vorhandene Dateien in einer neuen Version ohne Daten in den deaktivierten Zustand geladen werden können.  Im Idealfall kann ein VSPackage die Dateiformate früherer Versionen laden und speichern.  Falls dies nicht zutrifft, sollten Sie sich anbieten, das Dateiformat auf die neue Version VSPackages zu aktualisieren.  Das abwärts gerichtete dieses Ansatzes besteht darin, dass die aktualisierte Datei nicht in der Vorgängerversion geöffnet werden kann.  
  
 Um dieses Problem zu vermeiden, können Sie beim Ändern von Erweiterungen Dateiformate nicht kompatibel sind.  Beispielsweise könnte die Erweiterung, VSPackages Version 1 und Version 2 .mypkg10 konnte die Erweiterung, .mypkg20 verwenden.  Dieser Unterschied identifiziert ein VSPackage, der eine bestimmte Datei geöffnet.  Wenn Sie neueres VSPackages der Liste von Programmen hinzufügen, die mit einer alten Erweiterung zugeordnet sind, können Benutzer der rechten Maustaste auf die Datei, und wählen, ob sie in späteren VSPackages zu öffnen.  An diesem Punkt kann ein VSPackage, die Datei in das neue Format zu aktualisieren oder die Datei zu öffnen und die Kompatibilität mit früheren Versionen von VSPackages zu erhalten.  
  
> [!NOTE]
>  Sie können diese Ansätze kombinieren.  Sie können z. B. die Abwärtskompatibilität, indem Sie eine ältere Datei geladen und anbieten, das Dateiformat aktualisiert werden, wenn der Benutzer es speichert.  
  
## Das Problem wurde  
 Wenn Sie mehrere paralleles VSPackages die gleiche Erweiterung verwenden möchten, müssen Sie die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] auswählen, die mit der Erweiterung zugeordnet ist.  Es folgen zwei Alternativen:  
  
-   Öffnen Sie die Datei in der neuesten Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installierte auf dem Computer eines Benutzers.  
  
     In diesem Verfahren wird das Installationsprogramm zum Bestimmen der neuesten Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und im enthaltenden Registrierungseintrag, der für die Dateizuordnung geschrieben werden soll.  In einem Windows Installer\-Paket können Sie benutzerdefinierte Aktionen beinhalten, Festlegen einer Eigenschaft, die die letzte Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]angibt.  
  
    > [!NOTE]
    >  In diesem Kontext an „neuesten“ bedeutet „neueste unterstützte Version“. Diese Installationsprogramm erkennt nicht automatisch Einträge für eine nachfolgende Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Einträge in [Ermitteln von Systemanforderungen](../extensibility/internals/detecting-system-requirements.md) und [Befehle, die nach der Installation ausgeführt werden müssen](../extensibility/internals/commands-that-must-be-run-after-installation.md) sind ähnlich, die hier dargestellt werden und sind, zusätzliche Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]zu unterstützen, erforderlich.  
  
     Die folgenden Zeilen in der CustomActions\-Tabelle legen die DEVENV\_EXE\_LATEST\-Eigenschaft fest, um eine Eigenschaft durch die Tabellen und AppSearch RegLocator zu sein, die in [Befehle, die nach der Installation ausgeführt werden müssen](../extensibility/internals/commands-that-must-be-run-after-installation.md)erläutert wurden.  Zeilen in der InstallExecuteSequence\-Tabelle planen benutzerdefinierte Aktionen auszuführen zu einem frühen Zeitpunkt in der Sequenz.  Werte in der Spalte Bedingung der die Logik ausführen:  
  
    -   Visual Studio .NET 2002 ist die aktuelle Version, wenn sie die einzige aktuelle Version ist.  
  
    -   Visual Studio .NET 2003 ist die aktuelle Version nur, wenn sie vorhanden ist und [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht vorhanden ist.  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist die neueste Version, wenn sie die einzige aktuelle Version ist.  
  
     Der Nettoertrag besteht darin, dass DEVENV\_EXE\_LATEST den Pfad der neuesten Version von devenv.exe enthält.  
  
    ### CustomActions\-Tabellen von Zeilen, die die letzte Version von Visual Studio bestimmen  
  
    |Aktion|Typ|Quelle|Target|  
    |------------|---------|------------|------------|  
    |CA\_SetDevenvLatest\_2002|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2002\]|  
    |CA\_SetDevenvLatest\_2003|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2003\]|  
    |CA\_SetDevenvLatest\_2005|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2005\]|  
  
    ### InstallExecuteSequence\-Tabellen von Zeilen, die die letzte Version von Visual Studio bestimmen  
  
    |Aktion|Bedingung|Sequenz|  
    |------------|---------------|-------------|  
    |CA\_SetDevenvLatest\_2002|DEVENV\_EXE\_2002 AND NOT \(DEVENV\_EXE\_2003 OR DEVENV\_EXE\_2005\)|410|  
    |CA\_SetDevenvLatest\_2003|DEVENV\_EXE\_2003 AND NOT DEVENV\_EXE\_2005|420|  
    |CA\_SetDevenvLatest\_2005|DEVENV\_EXE\_2005|430|  
  
     Sie können die DEVENV\_EXE\_LATEST\-Eigenschaft in der Registrierung des Windows Installer\-Pakets Tabelle verwenden, um die HKEY\_CLASSES\_ROOT \\*ProgId*\\ Shell \\ zum Schreiben geöffnet BEFEHLSTASTE \\ der Standardwert " %1 „\[DEVENV\_EXE\_LATEST\]  
  
-   Lassen Sie ein freigegebenes programm Dialogfeldstartprogramm ausgeführt werden, das die beste Wahl der verfügbaren VSPackage\-Versionen treffen kann.  
  
     Die Entwickler von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] beschlossen diesen Ansatz, um die komplexen Anforderungen der mehrere Formate der Projektmappen zu behandeln und projektieren dass Ergebnis aus verschiedenen Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  In diesem Ansatz registrieren Sie ein Add\-In als programm Dialogfeldstartprogramm Ereignishandler.  Das Dialogfeldstartprogramm überprüft die Datei und entscheidet, der Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und VSPackages diese bestimmte Datei bearbeiten können.  Wenn beispielsweise ein Benutzer eine Datei geöffnet, die zuletzt von einer bestimmten Version von VSPackages gespeichert wurde, kann das Dialogfeldstartprogramm dieses VSPackage in der entsprechenden Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]starten.  Darüber hinaus kann ein Benutzer das Dialogfeldstartprogramm so konfigurieren, dass immer die neuesten Version zu starten.  Ein Dialogfeldstartprogramm kann auch einen Benutzer auffordern, das Format der Datei zu aktualisieren.  Wenn das Format der Datei eine Versionsnummer enthält, könnte das Dialogfeldstartprogramm einen Benutzer benachrichtigen, wenn das Dateiformat von einer Version ist, die später als ein oder mehrere des installierten VSPackages ist.  
  
     Das Dialogfeldstartprogramm sollte in einer Windows Installer\-Komponente sein, die mit allen Versionen von VSPackages freigegeben wird.  Dieser Prozess wird sichergestellt, dass immer die aktuellste Version installiert ist und wird nicht entfernt, bis alle Versionen von VSPackages deinstalliert werden.  Auf diese Weise werden die Dateizuordnungen und andere Registrierungseinträge Dialogfeldstartprogramm der Komponente beibehalten, auch wenn eine Version von VSPackages deinstalliert wird.  
  
## Deinstallieren und Datei\-Zuordnungen  
 VSPackage Deinstallieren, die Registrierungseinträge für Dateizuordnungen schreibt, entfernt die Dateizuordnungen.  Daher hat die Erweiterung keine zugeordneten Programme.  Windows Installer nicht“ „stellt die Registrierungseinträge wieder her, die hinzugefügt wurden, als ein VSPackage installiert wurde.  Im Folgenden sind einige Methoden, Dateizuordnungen eines Benutzers zu beheben:  
  
-   Mithilfe einer freigegebenen Komponente Dialogfeldstartprogramm, wie zuvor beschrieben.  
  
-   Weisen Sie den Benutzer auf, um eine Reparieren der Version von VSPackages auszuführen, das der Benutzer die Dateizuordnung besitzen sollen.  
  
-   Erstellen Sie ein separates ausführbares Programm bereit, die die entsprechenden Registrierungseinträge neu schreibt.  
  
-   Erstellen Sie eine optionsseite Konfiguration oder Dialogfeld bereit, mit deren Hilfe Benutzer Dateizuordnungen auswählen und verlorene Zuordnungen freigeben können.  Weisen Sie Benutzern, um die Deinstallation auszuführen.  
  
## Siehe auch  
 [Registrieren von Dateinamenerweiterungen für Seite\-an\-Seite\-Installationen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Registrieren von Verben für Dateinamenerweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)
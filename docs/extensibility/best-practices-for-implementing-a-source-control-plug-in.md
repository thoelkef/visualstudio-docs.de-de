---
title: "Bew&#228;hrte Methoden f&#252;r die Implementierung eines Datenquellen-Steuerelements-Plug-in | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bewährte Methoden für Source Control-Plug-ins"
  - "Best Practices Source Control-Plug-ins"
  - "Datenquellen-Steuerelement [Visual Studio SDK]-Plug-ins"
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Bew&#228;hrte Methoden f&#252;r die Implementierung eines Datenquellen-Steuerelements-Plug-in
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die folgenden technischen Details können Sie die zuverlässig ein Quellcodeverwaltungs\-Plug\-in implementieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Verwaltung von Speicherproblemen  
 In den meisten Fällen IDE \(IDE\), die der Aufrufer frei und reserviert. Das Quellcodeverwaltungs\-Plug\-Ins gibt Zeichenfolgen und anderen Elementen in der vom Aufrufer reservierte Puffer zurück. Ausnahmen werden in eine Beschreibung der Funktionen aufgeführt, in dem sie auftreten.  
  
## Arrays von Dateinamen  
 Wenn ein Array von Dateien übergeben wird, wird es nicht als ein fortlaufendes Array von Dateinamen übergeben. Es wird als ein Array von Zeigern auf Dateinamen übergeben. Z. B. in der [SccGet](../extensibility/sccget-function.md), werden die Dateinamen durch Übergeben der `lpFileNames` \-Parameter, in dem `lpFileNames` ist tatsächlich ein Zeiger auf eine `char **`.`lpFileNames`\[0\] ist ein Zeiger auf den Vornamen, `lpFileNames`\[1\] ist ein Zeiger auf den zweiten Namen und So weiter.  
  
## Großes Modell  
 Alle Zeiger sind 32 Bits, sogar auf 16\-Bit\-Betriebssysteme.  
  
## Vollqualifizierte Pfade  
 In dem Dateinamen oder Verzeichnisse als Argumente angegeben werden, wenn sie vollqualifizierte Pfade oder UNC\-Pfade, ohne das abschließende umgekehrte Schrägstriche. Es ist die Verantwortung für das Quellcodeverwaltungs\-Plug\-in in relative Pfade, wenn also eine Anforderung mit der zugrunde liegenden Quellcode\-Verwaltungssystem zu übersetzen.  
  
## Geben Sie einen vollqualifizierten Pfad für die registrierte DLL  
 Die IDE lädt die DLLs nicht mehr über relative Pfade \(z. B..\\NewProvider.dll\). Ein vollständiger Pfad der DLL muss \(z. B. C:\\Providers\\NewProvider.dll\) angegeben werden. Diese Anforderung erhöht die Sicherheit der IDE durch das Laden von nicht autorisierten oder imitierten Quellsteuerelement DLLs zu verhindern.  
  
## Überprüfen Sie bei der Installation des Plug\-in\-Datenquellen\-Steuerelements für eine vorhandene VSSCI\-Plug\-in  
 Ein Benutzer, der das Datenquellen\-Steuerelement\-Plug\-in installieren möchte möglicherweise bereits einen vorhandenen Quellcodeverwaltungssystem\-Plug\-in auf dem Computer installiert. Das Installationsprogramm \(Setup\) für das plug\-in die Erstellung sollte bestimmen, ob vorhandene Werte für die entsprechenden Registrierungsschlüssel vorhanden sind. Wenn diese Schlüssel bereits festgelegt sind, sollte das Installationsprogramm der Benutzer gefragt, ob das plug\-in als das Standard\-Datenquellen\-Steuerelement\-Plug\-in zu registrieren und zu ersetzen, das bereits installiert ist.  
  
## Ergebnis\-Fehlercodes und Reporting  
 Die `SCC_OK` Code für eine Source Control\-Funktion gibt an, dass der Vorgang, für alle Dateien erfolgreich war zurück. Wenn der Vorgang fehlschlägt, soll er ist den letzten Fehlercode gefunden zurückgeben.  
  
 Die Regel für die Berichterstattung ist, tritt ein Fehler in der IDE, die IDE für die Meldung zuständig ist. Tritt ein Fehler im Quellcode\-Verwaltungssystem, ist das Quellcodeverwaltungs\-Plug\-In für die Meldung verantwortlich. Z. B. würde "keine Dateien sind derzeit ausgewählte" von der IDE gemeldet während "Diese Datei bereits ausgecheckt ist" vom plug\-in gemeldet wird.  
  
## Context\-Struktur  
 Während des Aufrufs der [SccInitialize](../extensibility/sccinitialize-function.md), der Aufrufer übergibt der `ppvContext` \-Parameter, der eine nicht initialisierte Handle zu einer "void" ist. Das Quellcodeverwaltungs\-Plug\-in kann dieser Parameter ignoriert, oder eine Struktur jeglicher Art zuordnen und der übergebene Zeiger einen Zeiger zur Struktur abgelegt werden können. Die IDE diese Struktur nicht verstanden, aber übergibt einen Zeiger auf diese Struktur in jeden anderen Aufruf im plug\-in. Dies bietet wertvolle Cache Kontextinformationen, die dem plug\-in, globalen Zustandsinformationen zu verwalten, die bei Funktionsaufrufen beibehält, ohne die Verwendung von globalen Variablen verwendet werden kann. Das plug\-in ist verantwortlich für die Freigabe der Struktur bei einem Aufruf der [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Wenn im\-Plug\-in wird die `SCC_CAP_REENTRANT` bit im der [SccInitialize](../extensibility/sccinitialize-function.md) \(insbesondere in der `lpSccCaps` Parameter\), mehrere Kontext Strukturen werden verwendet, um alle Projekte zu verfolgen, die geöffnet sind.  
  
## Bitflags und anderen Befehlsoptionen  
 Für jeden Befehl wie z. B. die [SccGet](../extensibility/sccget-function.md), die IDE kann angeben, dass viele Optionen, die das Verhalten des Befehls zu ändern.  
  
 Die API unterstützt bestimmte Optionen von der IDE durch Festlegen der `fOptions` Parameter. Diese Optionen werden beschrieben [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md) zusammen mit den Befehlen, die sie betreffen. Im Allgemeinen sind diese Optionen für die der Benutzer nicht aufgefordert werden möchten.  
  
 Die meisten Benutzer konfigurierbare Einstellung Optionen sind nicht auf diese Weise definiert, denn sie zwischen Source Control\-Plug\-ins variieren. Aus diesem Grund empfohlen wird ein **Erweitert** Schaltfläche. In der **abrufen** Dialogfeld zeigt nur Informationen, die er versteht, aber es zeigt auch die IDE eine **Erweitert** Schaltfläche, wenn die Plug\-in\-Optionen für diesen Befehl ist. Klickt der Benutzer die **Erweitert** Schaltfläche, die IDE\-Aufrufe der [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) das Datenquellen\-Steuerelement, das der Benutzer Informationen, z. B. Bitflags oder ein Datum\/Uhrzeit\-Plug\-in aktivieren. Das plug\-in gibt diese Informationen in einer Struktur, die bei übergeben wird die `SccGet` Befehl.  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)   
 [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../extensibility/internals/creating-a-source-control-plug-in.md)
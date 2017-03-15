---
title: "Dialogfeld &quot;Befehlszeile f&#252;r Pr&#228;buildereignis&quot;/&quot;Befehlszeile f&#252;r Postbuildereignis&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEventsBuilder"
  - "vb.ProjectPropertiesBuildEventsBuilder"
helpviewer_keywords: 
  - "$(SolutionExt)"
  - "$(ProjectDir)"
  - "$(TargetPath)"
  - "$(ProjectExt)"
  - "$(TargetFileName)"
  - "$(PlatformName)"
  - "$(SolutionName)"
  - "Makros, Buildereignisse"
  - "$(SolutionPath)"
  - "$(ProjectPath)"
  - "$(ProjectFileName)"
  - "$(DevEnvDir)"
  - "$(TargetName)"
  - "$(TargetDir)"
  - "$(SolutionDir)"
  - "$(TargetExt)"
  - "$(OutDir)"
  - "$(ConfigurationName)"
  - "$(SolutionFileName)"
  - "$(ProjectName)"
  - "Buildereignisse, Makros"
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Dialogfeld &quot;Befehlszeile f&#252;r Pr&#228;buildereignis&quot;/&quot;Befehlszeile f&#252;r Postbuildereignis&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sie können Präbuildereignisse und Postbuildereignisse für den [Seite "Buildereignisse", Projekt\-Designer \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md) direkt in das Bearbeitungsfeld eingeben oder Präbuildmakros und Postbuildmakros aus einer Liste verfügbarer Makros auswählen.  
  
> [!NOTE]
>  Präbuildereignisse werden nicht ausgeführt, wenn das Projekt aktuell ist und kein Build ausgelöst wird.  
  
## Liste der Elemente der Benutzeroberfläche  
 **Bearbeitungsfeld der Befehlszeile**  
 Enthält die Ereignisse, die vor oder nach dem Build ausgeführt werden.  
  
> [!NOTE]
>  Fügen Sie vor allen Postbuildbefehlen, die BAT\-Dateien ausführen, eine `call`\-Anweisung hinzu.  Beispielsweise `call C:\MyFile.bat` oder `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Makros**  
 Erweitert das Bearbeitungsfeld, um eine Liste der Makros anzuzeigen, die in das Bearbeitungsfeld der Befehlszeile eingefügt werden.  
  
 **Makrotabelle**  
 Listet die verfügbaren Makros und ihren jeweiligen Wert auf.  Eine Beschreibung der einzelnen Makros finden Sie nachfolgend unter Makros.  Sie können jeweils nur ein Makro auswählen, das in das Bearbeitungsfeld der Befehlszeile eingefügt werden soll.  
  
 **Insert**  
 Fügt das in der Makrotabelle ausgewählte Makro in das Bearbeitungsfeld der Befehlszeile ein.  
  
### Makros  
 Mit diesen Makros können Sie den Speicherort von Dateien festlegen oder den tatsächlichen Namen der Eingabedatei abrufen, falls mehrere Elemente ausgewählt wurden.  Bei den Makros wird keine Groß\-\/Kleinschreibung berücksichtigt.  
  
|Makro|Beschreibung|  
|-----------|------------------|  
|`$(ConfigurationName)`|Der Name der aktuellen Projektkonfiguration, z. B. "Debug".|  
|`$(OutDir)`|Pfad des Verzeichnisses für Ausgabedateien, bezogen auf das Projektverzeichnis.  Wird in den Wert für die Eigenschaft Ausgabeverzeichnis aufgelöst.  Enthält den nachgestellten umgekehrten Schrägstrich \('\\'\).|  
|`$(DevEnvDir)`|Installationsverzeichnis von Visual Studio \(definiert mit Laufwerk und Pfad\); enthält einen nachgestellten umgekehrten Schrägstrich \("\\"\).|  
|`$(PlatformName)`|Der Name der aktuellen Zielplattform.  Beispielsweise "AnyCPU".|  
|`$(ProjectDir)`|Das Verzeichnis des Projekts \(mit definiertem Laufwerk und Pfad\); enthält den nachgestellten umgekehrten Schrägstrich \('\\'\).|  
|`$(ProjectPath)`|Der absolute Pfadname des Projekts \(mit definiertem Laufwerk, Pfad, Basisnamen und definierter Dateierweiterung\).|  
|`$(ProjectName)`|Der Basisname des Projekts.|  
|`$(ProjectFileName)`|Der Dateiname des Projekts \(mit definiertem Basisnamen und definierter Dateierweiterung\).|  
|`$(ProjectExt)`|Die Dateierweiterung des Projekts.  Enthält den Punkt \('.'\) vor der Dateierweiterung.|  
|`$(SolutionDir)`|Das Verzeichnis der Projektmappe \(mit definiertem Laufwerk und Pfad\); enthält den nachgestellten umgekehrten Schrägstrich \('\\'\).|  
|`$(SolutionPath)`|Der absolute Pfadname der Projektmappe \(mit definiertem Laufwerk, Pfad, Basisnamen und definierter Dateierweiterung\).|  
|`$(SolutionName)`|Der Basisname der Projektmappe.|  
|`$(SolutionFileName)`|Der Dateiname der Projektmappe \(mit definiertem Basisnamen und definierter Dateierweiterung\).|  
|`$(SolutionExt)`|Die Dateierweiterung der Projektmappe.  Enthält den Punkt \('.'\) vor der Dateierweiterung.|  
|`$(TargetDir)`|Das Verzeichnis der primären Ausgabedatei für das Build \(mit definiertem Laufwerk und Pfad\).  Enthält den nachgestellten umgekehrten Schrägstrich \('\\'\).|  
|`$(TargetPath)`|Der absolute Pfadname der primären Ausgabedatei für das Build \(mit definiertem Laufwerk, Pfad, Basisnamen und definierter Dateierweiterung\).|  
|`$(TargetName)`|Der Basisname der primären Ausgabedatei für den Build.|  
|`$(TargetFileName)`|Der Dateiname der primären Ausgabedatei für das Build \(als Basisname und Dateierweiterung definiert\).|  
|`$(TargetExt)`|Die Dateierweiterung der primären Ausgabedatei für den Build.  Enthält den Punkt \('.'\) vor der Dateierweiterung.|  
  
## Siehe auch  
 [Angeben von benutzerdefinierten Build\-Ereignissen in Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)   
 [Seite "Buildereignisse", Projekt\-Designer \(C\#\)](../../ide/reference/build-events-page-project-designer-csharp.md)   
 [Gewusst wie: Festlegen von Buildereignissen \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Gewusst wie: Angeben von Buildereignissen \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)
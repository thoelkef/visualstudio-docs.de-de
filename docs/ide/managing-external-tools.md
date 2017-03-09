---
title: "Verwalten von externen Tools | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.externaltools"
helpviewer_keywords: 
  - "ActiveX-Steuerelementtestcontainer"
  - "ATL Trace-Tool"
  - "ATLTraceTool.exe"
  - "Bind-Tool"
  - "GUID erstellen (Tool)"
  - "DisableMsg-Tool"
  - "ErrLook-Tool"
  - "Fehlersuchtool"
  - "Externe Tools [Visual Studio]"
  - "GUIDGEN-Tool"
  - "HCW (Help Workshop)"
  - "Help Workshop"
  - "IDL-Compiler"
  - "Local Test Manager"
  - "LTM (Local Test Manager)"
  - "MAKEHM-Tool"
  - "mc (Message Compiler)"
  - "Message Compiler [Visual Studio]"
  - "MIDL, Externe Tools"
  - "Midlc (IDL-Compiler)"
  - "MkTypLib-Tool"
  - "ODBC-Test"
  - "Odbcte32.exe"
  - "Odbcte32w.exe"
  - "OLE DB Rowset Viewer"
  - "OLE/COM-Objektkatalog"
  - "OLEVIEW (Objektkatalog)"
  - "RC (Ressourcencompiler)"
  - "ReBase-Tool"
  - "Ressourcencompiler"
  - "RowsetViewer-Tool"
  - "Tools [Visual Studio], Extern"
  - "tstcon32.exe"
  - "Type Library Generator"
  - "undname.exe"
  - "Dienstprogramme, Externe Tools"
  - "UUID-Generator"
  - "Uuidgen.exe"
  - "Vcspawn.exe"
  - "Vsvars32.bat"
  - "WebDbg-Tool"
  - "Windows NT C++ Symbol Undecorator"
  - "Windows NT Image Binder"
  - "Windows NT Image Rebaser"
  - "Windows NT Message Compiler"
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
caps.handback.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Verwalten von externen Tools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können externe Tools aus Visual Studio aufrufen.  Einige Standardtools sind im Menü **Extras** verfügbar, Sie können jedoch andere eigene ausführbare Dateien hinzufügen.  
  
## Im Menü "Extras" von Visual Studio verfügbare Tools  
 Sie können die folgenden Tools in  **im Menü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Extras** aufrufen.  Sie können sie auch nach Namen im Fenster **Schnellstart** aufrufen.  Um beispielsweise die Datei "GuidGen.exe" aufzurufen, geben Sie "GUID erstellen" ein.  
  
1.  GUID erstellen: Generiert eine GUID.  
  
2.  Fehlersuche: Empfängt eine Fehlermeldung vom eingegebenen Wert.  Weitere Informationen finden Sie unter [ERRLOOK\-Referenz](/visual-cpp/build/reference/errlook-reference).  
  
3.  ATL\-\/MFC\-Ablaufverfolgungsprogramm: Zeigt Debugablaufverfolgungs\-Meldungen in den ATL\- und MFC\-Quellen an.  
  
4.  PreEmptive Dotfuscator und Analytics: Schützt .NET\-Programme gegen Reverse Engineering.  
  
5.  SPY\+\+: Stellt Prozesse, Threads, Fenster und Fenstermeldungen grafisch dar.  
  
6.  WCF\-Dienstkonfigurations\-Editor: Ermöglicht es Ihnen, die Konfigurationseinstellungen für WCF\-Dienste zu erstellen und zu ändern.  
  
> [!WARNING]
>  Je nach installierter Visual Studio\-Edition und angewendetem Einstellungsprofil wird möglicherweise eine andere Liste mit externen Tools angezeigt.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Hinzufügen von neuen Tools  
 So können im Menü **Extras** ein externes Tool hinzufügen.  Öffnen Sie das Dialogfeld **Externe Tools**, und klicken Sie auf **Hinzufügen**. Geben Sie dann die Informationen ein.  Beispielsweise führt der folgende Eintrag dazu, dass Windows Explorer in dem Verzeichnis der Datei geöffnet wird, das Sie zurzeit in Visual Studio geöffnet haben:  
  
1.  Titel: Dateispeicherort öffnen  
  
2.  Befehl: explorer.exe  
  
3.  Argumente: \/root, "$\(ItemDir\)"  
  
## Argumente für externe Tools  
 Bei den folgenden Argumente handelt es sich um Visual Studio\-Variablen, beim Starten eines externen Tools zugewiesen werden.  Links zu externen Tools, z. B. Editor oder Spy\+\+, können im Menü **Extras** mithilfe des Dialogfelds "Externe Tools" aufgeführt werden.  
  
> [!NOTE]
>  In der IDE\-Statusleiste werden die Variablen "Aktuelle Zeile" und "Aktuelle Spalte" angezeigt, um die Position der Einfügemarke im aktiven Code\-Editor anzuzeigen.  Die Variable "Aktueller Text" gibt den an dieser Stelle ausgewählten Text oder Code zurück.  
  
|Name|Argument|Beschreibung|  
|----------|--------------|------------------|  
|Elementpfad|$\(ItemPath\)|Der vollständige Dateiname der aktuellen Datei \(Laufwerk \+ Pfad \+ Dateiname\).|  
|Elementverzeichnis|$\(ItemDir\)|Das Verzeichnisses der aktuellen Datei \(Laufwerk \+ Pfad\).|  
|Elementdateiname|$\(ItemFilename\)|Der Dateiname der aktuellen Datei \(Dateiname\).|  
|Elementerweiterung|$\(ItemExt\)|Die Dateinamenerweiterung der aktuellen Datei..|  
|Aktuelle Zeile|&\(CurLine\)|Die aktuelle Zeilenposition des Cursors im Codefenster.|  
|Aktuelle Spalte|&\(CurCol\)|Die aktuelle Spaltenposition des Cursors im Codefenster.|  
|Aktueller Text|&\(CurText\)|Der ausgewählte Text.|  
|Zielpfad|$\(TargetPath\)|Der vollständige Dateiname des zu erstellenden Elements \(Laufwerk \+ Pfad \+ Dateiname\).|  
|Target Directory|$\(TargetDir\)|Das Verzeichnis des zu erstellenden Elements.|  
|Target Name|$\(TargetName\)|Der Dateiname des zu erstellenden Elements.|  
|Zielerweiterung|$\(TargetExt\)|Die Dateinamenerweiterung zu erstellenden Elements.|  
|Binäres Verzeichnis|$\(BinDir\)|Der endgültige Position der Binärdatei, die erstellt wird \(als Laufwerk \+ Pfad definiert\).  Beispiel: \\...\\Eigene Dateien\\ Visual Studio\-\<Version \>\\\<ProjectName\>\\bin\\debug|  
|Projektverzeichnis|$\(ProjDir\)|Das Verzeichnisses des aktuellen Projekts \(Laufwerk \+ Pfad\).|  
|Projektdateiname|$\(ProjFileName\)|Der Dateiname des aktuellen Projekts \(Laufwerk \+ Pfad \+ Dateiname\).|  
|Projektmappenverzeichnis|$\(SolutionDir\)|Das Verzeichnisses der aktuellen Projektmappe \(Laufwerk \+ Pfad\).|  
|Projektmappen\-Dateiname|$\(SolutionFileName\)|Der Dateiname der aktuellen Projektmappe \(Laufwerk \+ Pfad \+ Dateiname\).|  
  
## Siehe auch  
 [C\/C\+\+\-Buildtools](/visual-cpp/build/reference/c-cpp-build-tools)
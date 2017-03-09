---
title: Verwalten externer Tools | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 66e09a22bcedb37f82eb9517a8f9d4affbe3a374
ms.openlocfilehash: ad9461bb29dba3e8e2ffe242c1f709587729ce22
ms.lasthandoff: 02/22/2017

---
# <a name="manage-external-tools"></a>Verwalten externer Tools
Sie können externe Tools aus Visual Studio aufrufen. Einige Standardtools sind im Menü **Extras** verfügbar, Sie können jedoch andere eigene ausführbare Dateien hinzufügen.  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Im Menü „Extras“ von Visual Studio verfügbare Tools
 Sie können die folgenden Tools in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im Menü **Extras** aufrufen. Sie können sie auch nach Namen im Fenster **Schnellstart** aufrufen. Um beispielsweise die Datei „GuidGen.exe“ aufzurufen, geben Sie **GUID erstellen** ein.  
  
1.  GUID erstellen: Generiert eine GUID.  
  
2.  Fehlersuche: Empfängt eine Fehlermeldung vom eingegebenen Wert. Weitere Informationen finden Sie unter [ERRLOOK-Referenz](/visual-cpp/build/reference/errlook-reference).  
  
3.  ATL-/MFC-Ablaufverfolgungsprogramm: Zeigt Debugablaufverfolgungs-Meldungen in den ATL- und MFC-Quellen an.  
  
4.  PreEmptive Dotfuscator und Analytics: Schützt .NET-Programme gegen Reverse Engineering.  
  
5.  SPY++: Stellt Prozesse, Threads, Fenster und Fenstermeldungen grafisch dar.  
  
6.  WCF-Dienstkonfigurations-Editor: Ermöglicht es Ihnen, die Konfigurationseinstellungen für WCF-Dienste zu erstellen und zu ändern.  
  
> [!WARNING]
>  Je nach installierter Visual Studio-Edition und angewendetem Einstellungsprofil wird möglicherweise eine andere Liste mit externen Tools angezeigt. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="add-new-tools-to-the-tools-menu"></a>Neue Tools zum Menü „Extras“ hinzufügen 
 So können im Menü **Extras** ein externes Tool hinzufügen. Öffnen Sie das Dialogfeld **Externe Tools**, und klicken Sie auf **Hinzufügen**. Geben Sie dann die Informationen ein. Beispielsweise führt der folgende Eintrag dazu, dass Windows Explorer in dem Verzeichnis der Datei geöffnet wird, das Sie zurzeit in Visual Studio geöffnet haben:  
  
1.  Titel: Dateispeicherort öffnen  
  
2.  Befehl: explorer.exe  
  
3.  Argumente: /root, "$(ItemDir)"  
  
## <a name="arguments-for-external-tools"></a>Argumente für externe Tools  
 Bei den folgenden Argumente handelt es sich um Visual Studio-Variablen, beim Starten eines externen Tools zugewiesen werden. Links zu externen Tools, z.B. Editor oder Spy++, können im Menü **Extras** mithilfe des Dialogfelds „Externe Tools“ aufgeführt werden.  
  
> [!NOTE]
>  In der IDE-Statusleiste werden die Variablen "Aktuelle Zeile" und "Aktuelle Spalte" angezeigt, um die Position der Einfügemarke im aktiven Code-Editor anzuzeigen. Die Variable "Aktueller Text" gibt den an dieser Stelle ausgewählten Text oder Code zurück.  
  
|Name|Argument|Beschreibung|  
|----------|--------------|-----------------|  
|Elementpfad|$(ItemPath)|Der vollständige Dateiname der aktuellen Datei (Laufwerk + Pfad + Dateiname).|  
|Elementverzeichnis|$(ItemDir)|Das Verzeichnisses der aktuellen Datei (Laufwerk + Pfad).|  
|Elementdateiname|$(ItemFilename)|Der Dateiname der aktuellen Datei (Dateiname).|  
|Elementerweiterung|$(ItemExt)|Die Dateinamenerweiterung der aktuellen Datei..|  
|Aktuelle Zeile|&(CurLine)|Die aktuelle Zeilenposition des Cursors im Codefenster.|  
|Aktuelle Spalte|&(CurCol)|Die aktuelle Spaltenposition des Cursors im Codefenster.|  
|Aktueller Text|&(CurText)|Der ausgewählte Text.|  
|Zielpfad|$(TargetPath)|Der vollständige Dateiname des zu erstellenden Elements (Laufwerk + Pfad + Dateiname).|  
|Target Directory|$(TargetDir)|Das Verzeichnis des zu erstellenden Elements.|  
|Target Name|$(TargetName)|Der Dateiname des zu erstellenden Elements.|  
|Zielerweiterung|$(TargetExt)|Die Dateinamenerweiterung zu erstellenden Elements.|  
|Binäres Verzeichnis|$(BinDir)|Der endgültige Position der Binärdatei, die erstellt wird (als Laufwerk + Pfad definiert). Beispiel: **\\...\Eigene Dateien\ Visual Studio-\<Version >\\<ProjectName\>\bin\debug**|  
|Projektverzeichnis|$(ProjDir)|Das Verzeichnisses des aktuellen Projekts (Laufwerk + Pfad).|  
|Projektdateiname|$(ProjFileName)|Der Dateiname des aktuellen Projekts (Laufwerk + Pfad + Dateiname).|  
|Projektmappenverzeichnis|$(SolutionDir)|Das Verzeichnisses der aktuellen Projektmappe (Laufwerk + Pfad).|  
|Projektmappen-Dateiname|$(SolutionFileName)|Der Dateiname der aktuellen Projektmappe (Laufwerk + Pfad + Dateiname).|  
  
## <a name="see-also"></a>Siehe auch  
 [C/C++-Buildtools](/visual-cpp/build/reference/c-cpp-build-tools)


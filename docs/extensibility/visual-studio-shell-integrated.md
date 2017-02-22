---
title: "Visual Studio-Shell (integriert) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Shell, integrierten Modus-Funktionen"
  - "Funktionen des integrierten Modus-Shell [Visual Studio]"
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio-Shell (integriert)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio integrierte Shell enthält die integrierten Entwicklungsumgebung \(IDE\), Debugger und Quellcode\-Verwaltungsanbieter. Keine Programmiersprache ist enthalten. Die integrierte Shell stellt jedoch ein Framework bereit, die Sie Programmiersprachen hinzufügen können.  
  
 Visual Studio integrierte Shell ist tatsächlich eine Kombination von Visual Studio isolated Shell plus eine zusätzliche Installation integrierte Shell bestimmte Komponenten einzuschließen.  Die integrierte Shell\-Anwendung sollten beide das isolierte Shell redistributable Package vom enthalten [Microsoft Visual Studio Shell \(isoliert\) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022) sowie die integrierte Shell verteilbares Paket [Microsoft Visual Studio Shell \(integriert\) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Bevor Sie die verteilbaren Pakete für isolierte und integrierte Shell zugreifen können, werden Sie aufgefordert, eine kurze Umfrage ausfüllen.  Nach dem Ausfüllen der Umfrage teilnehmen, werden Sie zu Visual Studio Connect Downloadlinks verteilbare Paket weitergeleitet.  Die Downloadlinks finden Sie bei nachfolgenden Besuchen der Visual Studio Connect\-Website unter der **Programme &#124; VISUAL STUDIO 2015 integriert und ISOLIERTE SHELL** Registerkarte.  
  
 Wenn Sie die integrierte Shell\-Anwendung auf dem gleichen Computer wie die Vollversion von Visual Studio installieren, werden die Anwendung Komponenten direkt in Visual Studio integriert werden.  
  
## Funktionen in die integrierte Shell  
  
|||  
|-|-|  
|Funktionsbereich|Funktion|  
|Sprachunterstützung|-   Keine|  
|IDE|<ul><li>Einstellungen<br /><br /> <ul><li>Erstellen von Einstellungen</li><li>Importieren und Exportieren von Einstellungen</li><li>Zurücksetzen</li></ul></li><li>**Toolbox** Integration</li><li>**Aufgabenliste** Integration</li><li>Integration von Hilfe</li><li>**Optionen** \(Dialogfeld\)</li><li>Verwaltung von Schriftarten und Farben</li><li>**Ausgabe** Fenster</li><li>**Befehl** Fenster</li><li>Fensterverwaltung</li><li>Befehle, Menüs und Tastenkombinationen</li><li>Domänenspezifische Sprache \(DSL\)\-Laufzeit</li></ul>|  
|Projektsystem und Projekttypen|-   Projektmappen und Projektmappenordner<br />-   Projektmappen\-Konfigurations\-manager<br />-   Verwalten von<br />-   Lösungen für einzelne Projekt und mit mehreren Projekten<br />-   Application\-Designer \(vereinfachte Projekteigenschaften\)<br />-   Webverweis hinzufügen<br />-   Dienstverweis hinzufügen<br />-   Single\-Projekt<br />-   Website\-Projekttypen<br />-   Webanwendungsprojekte|  
|Build|-   Benutzerdefinierte Schritte in der IDE<br />-   Vorkompilierung für den Schutz des geistigen Eigentums \(IP\)<br />-   Signieren von Code<br />     MSBuild|  
|Editor|-   Tools \(unified suchen, Datenquellendefinition, Vererbung\) Durchsuchen von Code<br />-   Navigieren in Code<br />-   IntelliSense<br />-   SmartTags<br />-   Umgestaltung<br />-   Einrückung<br />-   IntelliSense\-Filtern<br />-   **Codedefinition** Fenster|  
|Designer|-   Windows Presentation Foundation\-Designer<br />-   Windows Forms\-Designer<br />-   Web\-Designer und HTML\-Editor|  
|Daten|-   **Server\-Explorer** \(Vereinfachtes: nur Daten\). Siehe Hinweis 1.<br />-   **Datenquellen** Fenster<br />-   Vollständigen Satz von Steuerelementen von<br />-   XML\-Editor<br />-   Bindet Daten an die lokale Datenquelle \(. MDF\-Datei oder. MDB\)<br />-   Daten binden an Objekt<br />-   Daten binden an Web service<br />-   Bindet Daten an den lokalen Datenbankserver<br />-   Bindet Daten an remote\-Datenbankserver<br />-   DDL\-Tools für remote\-Daten<br />-   **Server\-Explorer** Erweiterbarkeit \([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Beispiele\)|  
|Debugger|-   Lokales Debuggen. Siehe Hinweis 2.<br />-   Verwaltetes Debuggen<br />-   Lokales Debuggen<br />-   An lokalen Prozess anfügen<br />-   Fügen an Prozesse an<br />-   Anonyme Delegaten<br />-   Anwendungsdomänen<br />-   ASPX\-Debuggen<br />-   Attribute<br />-   Unterbrechen Sie während der eval\-Funktion<br />-   Haltepunkte<br />-   Haltepunkt\-Einschränkungen<br />-   Aufrufliste<br />-   **Befehl** Fenster<br />-   Threadübergreifende Debuggen<br />-   Datentipps<br />-   Daten\-Schnellansicht<br />-   Debugger\-Support für verwaltetes Debuggen \(MDAs\)<br />-   Debugger\-Support für Typ\-Weiterleitung<br />-   DTEEvents\-Unterstützung für OTB<br />-   JMC zugeordnetem<br />-   Debugger AppID Test \(DBGCLR\)<br />-   Debugger\-Profil<br />-   Debuggertools und Optionen<br />-   Iterator\-Debuggen<br />-   Ausdrucksauswertung zur Entwurfszeit<br />-   C\#\-Ausdrucksauswerter<br />-   Disassemblierung<br />-   Bearbeiten und Fortfahren<br />-   Expression Evaluator Windows \(lokal, Überwachung Auto\)<br />-   Ausnahmen\-Hilfe<br />-   Ausnahmen<br />-   Ausführung<br />-   Generika<br />-   Abrufen des richtigen Quellcode<br />-   Debuggen von HPC\-Cluster<br />-   Integriertes Debuggen mehrerer Sprachen<br />-   Interop\-Debuggen<br />-   Just\-in\-Time\-Debuggen<br />-   Lokales Debuggen<br />-   Verwaltetes Debuggen<br />-   Manuelle Steuerung \(Fenster Prozesse\)<br />-   Arbeitsspeicher<br />-   MiniDump\-Unterstützung<br />-   Module<br />-   Mehrere Prozesse debuggen.<br />-   Systemeigenes Debuggen<br />-   Neue Debug\-Engine\-Unterstützung<br />-   Debuggen von optimiertem code<br />-   Im Ausgabefenster filtern<br />-   Prozess\-hosting für verwaltetes Debuggen<br />-   Prozesse<br />-   Aktuellen Wert anzeigen<br />-   Register<br />-   Register im Stapel<br />-   Remotedebuggen<br />-   Rückgabewert<br />-   Debuggen von Skripts<br />-   Unterstützung von Datenquellen<br />-   Sicherheit<br />-   Seite\-an\-Seite<br />-   SQL<br />-   Symbolserver<br />-   Ablaufverfolgungspunkte<br />-   Thread<br />-   Visualisierungen<br />-   Extensible Stylesheet Language Transformations \(XSLT\)\-debugger|  
|64\-Bit\-Unterstützung|-   64\-Bit\-Debuggen für verwalteten und systemeigenen Code, alle Sprachen<br />-   Unterstützung von X 64 native|  
|Source Code Control \(SCC\)|-   Grundlegende SCC\-Integration. Siehe Hinweis 3.<br />-   Überprüfung der Tools und Optionen|  
|Erweiterungen|-   Nutzung von VSPackages und MEF\-Komponenten|  
  
## Notizen  
  
#### 1. Data Tools  
 Die integrierte Shell enthält Datenbank\-Entwicklungstools, wie die Unterstützung der Erweiterbarkeit und die vereinfachte **Projektmappen\-Explorer**. Allerdings sind SQL Server Express, SQL Reporting und Crystal Reports in der integrierten Shell nicht enthalten.  
  
#### 2. Debugunterstützung  
 Die integrierte Shell enthält die gleichen Debugmodul, die in der Community\-Version von Visual Studio enthalten ist. Debugmoduls enthält den allgemeinen Debugger für verwalteten Code sowie verwandten Funktionen, wie z. B. ausführen, anfügen, Haltepunkt festlegen, bearbeiten und Fortfahren sowie andere. Allerdings unterstützt Debugmoduls Debuggen von SQL Server\-Datenbank nicht.  
  
 Obwohl Unterstützung für systemeigenes Debuggen in der grundlegenden Debuggerpaket enthalten ist, können nicht erweitert werden, um weitere Sprachen zu unterstützen.  
  
#### 3. Integration der Quellcodeverwaltung  
 Die integrierte Shell stellt APIs bereit, für die Implementierung der Source Code Control \(SCC\) und für die Bereitstellung von des MSSCCI\-basierte allgemeine Quellsteuerelement Integrationskomponenten.  
  
 SCC\-Integration ist, zwar nicht die Pro\-Edition von Visual Studio ein regelmäßiger wird die SCC\-Integration in die integrierte Shell bereitgestellt.  
  
#### 4. Build\-Unterstützung  
 Die integrierte Shell unterstützt Build. Sie können Informationen zu Builds, in dem [MSBuild Reference](../msbuild/msbuild-reference.md).  
  
## Die integrierte Shell nicht enthaltene Features  
 Im folgenden finden eine Liste der Funktionen, die nicht in der integrierten Shell enthalten sind:  
  
-   Klassen\-Designer  
  
-   Vorbeugender DotFuscator  
  
-   Sprachfunktionen  
  
-   VSHost  
  
-   In der integrierten Shell sind keine Visual Studio\-Sprachen oder ihre zugeordneten Projektvorlagen oder Projektelementvorlagen enthalten. Keine sprachspezifischen Implementierungen von anderen Funktionen sind enthalten, wird Visual Basic\-Codeausschnitte.  
  
## Siehe auch  
 [Übersicht über die Erweiterung von Visual Studio](../Topic/Extending%20Visual%20Studio%20Overview.md)
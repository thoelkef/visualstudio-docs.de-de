---
title: Visual Studio-Shell (integriert) | Microsoft-Dokumentation
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 4f2ddbc47f9a014acde2850dba5c72ef3a784847
ms.openlocfilehash: 8edd3a6fcca0c2ddd4d580f0874b737cfbbc40c9
ms.lasthandoff: 03/01/2017

---
# <a name="visual-studio-shell-integrated"></a>Visual Studio-Shell (integriert)
Visual Studio integrierte Shell enthält die integrierten Entwicklungsumgebung (IDE), Debugger und Quellcode-Verwaltungsanbieter. Keine Programmiersprache ist enthalten. Die integrierte Shell stellt jedoch ein Framework bereit, die Sie Programmiersprachen hinzufügen können.  
  
 Visual Studio integrierte Shell ist tatsächlich eine Kombination von Visual Studio isolated Shell plus eine zusätzliche Installation integrierte Shell bestimmte Komponenten einzuschließen.  Die integrierte Shell-Anwendung sollten beide das isolierte Shell redistributable Package vom enthalten [Microsoft Visual Studio Shell (isoliert) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022) sowie die integrierte Shell verteilbares Paket [Microsoft Visual Studio Shell (integriert) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Bevor Sie die verteilbaren Pakete für isolierte und integrierte Shell zugreifen können, werden Sie aufgefordert, eine kurze Umfrage ausfüllen.  Nach dem Ausfüllen der Umfrage teilnehmen, werden Sie zu Visual Studio Connect Downloadlinks verteilbare Paket weitergeleitet.  Sie finden die Downloadlinks bei nachfolgenden Besuchen der Visual Studio Connect-Website unter der **Programme | VISUAL STUDIO 2015 integriert und ISOLIERTE SHELL** Registerkarte.  
  
 Wenn Sie die integrierte Shell-Anwendung auf dem gleichen Computer wie die Vollversion von Visual Studio installieren, werden die Anwendung Komponenten direkt in Visual Studio integriert werden.  
  
## <a name="features-in-the-integrated-shell"></a>Funktionen in die integrierte Shell  
  
|||  
|-|-|  
|Funktionsbereich|Funktion|  
|Sprachunterstützung|-Keine|  
|IDE|<ul><li>Einstellungen<br /><br /> <ul><li>Erstellen von Einstellungen</li><li>Importieren und Exportieren von Einstellungen</li><li>Zurücksetzen</li></ul></li><li>**Toolbox** Integration</li><li>**Aufgabenliste** Integration</li><li>Integration von Hilfe</li><li>**Optionen** (Dialogfeld)</li><li>Verwaltung von Schriftarten und Farben</li><li>**Ausgabe** Fenster</li><li>**Befehl** Fenster</li><li>Fensterverwaltung</li><li>Befehle, Menüs und Tastenkombinationen</li><li>Domänenspezifische Sprache (DSL)-Laufzeit</li></ul>|  
|Projektsystem und Projekttypen|-Lösungen und Projektmappenordner<br />-Konfigurations-Manager Lösung<br />-Item management<br />-Lösungen Single-Projekt und mit mehreren Projekten<br />-Anwendungsentwicklern (vereinfachte Projekteigenschaften)<br />-Webverweis hinzufügen<br />-Hinzufügen eines Dienstverweises<br />-Single-Projekt<br />-Website Projekttypen<br />-Webanwendungsprojekte|  
|Build|-Benutzerdefinierte Buildschritte in IDE<br />– Vorkompilierung für den Schutz des geistigen Eigentums (IP)<br />-Codesignatur<br />     MSBuild|  
|Editor|-Durchsuchen von Tools (unified suchen, Datenquellendefinition, Vererbung) von code<br />-Code navigation<br />-IntelliSense<br />-SmartTags<br />-Umgestaltung<br />-Einrückung<br />-IntelliSense Filtern<br />-   **Code Definition** Fenster|  
|Designer|-Windows Presentation Foundation-Designer<br />-Windows Forms-Designer<br />-Web-Designer und HTML-Editor|  
|Daten|-   **Server-Explorer** (Vereinfachtes: nur Daten). Siehe Hinweis 1.<br />-   **Datenquellen** Fenster<br />-Vollständiger Satz von Steuerelementen von<br />-XML-Editor<br />-Daten binden, um lokale Datenquelle (. MDF-Datei oder. MDB)<br />-Data-Bind Objekt<br />-Bindet Daten an den Webdienst<br />-Bindet Daten an den lokalen Datenbankserver<br />-Daten binden, um remote-Datenbankserver<br />-DDL Tools für remote-Daten<br />-   **Server-Explorer** Erweiterbarkeit ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Beispiele)|  
|Debugger|-Lokales Debuggen. Siehe Hinweis 2.<br />-Bei verwaltetem Debuggen<br />-Lokales Debuggen<br />– An den lokalen Prozess anhängen.<br />-Remoteprozess zuordnen<br />-Anonymen Delegaten<br />-Anwendungsdomänen<br />-ASPX Debuggen<br />-Attribute<br />-Unterbrechen Sie während der eval-Funktion<br />-Haltepunkte<br />-Haltepunkt Einschränkungen<br />-Aufrufliste<br />-   **Befehl** Fenster<br />-Debuggen Cross-thread<br />-Datentipps<br />-Daten Schnellansicht<br />-Debugger Unterstützung für verwaltetes Debuggen (MDAs)<br />-Debugger Unterstützung für Typ-Weiterleitung<br />-DTEEvents Unterstützung für OTB<br />-JMC zugeordnetem<br />-Debugger AppID Test (DBGCLR)<br />-Debugger Profil<br />-Debugger-Tools und Optionen<br />-Iterator debugging<br />-Entwurfszeit-Auswertung von Ausdrücken<br />-C#-Ausdrucksauswerter<br />-Disassembly<br />-Bearbeiten und fortfahren<br />-Expression Evaluator Windows (lokal, Überwachung Auto)<br />-Ausnahmen-Hilfe<br />-Ausnahmen<br />-Ausführung<br />-Generika<br />-Richtige Quelle abrufen<br />HPC/clusterdebugging<br />-Integrierte Debuggen mehrerer Sprachen<br />-Interop-Debuggen<br />-Just-in-Time-Debuggen<br />-Lokales Debuggen<br />-Bei verwaltetem Debuggen<br />-Die manuelle Steuerung (Fenster Prozesse)<br />-Arbeitsspeicher<br />-MiniDump Unterstützung<br />-Module<br />-Mehrere Prozesse debuggen.<br />-Systemeigenes Debuggen<br />-Neue Debug-Engine-Unterstützung<br />-Optimierten Codedebuggen.<br />-Ausgabe Windows-Filterung<br />– Verarbeiten Sie hosting für verwaltetes Debuggen<br />-Prozesse<br />-Schnellüberwachung<br />-Register<br />-Register Stapel<br />-Remote-debugging<br />-Rückgabewerte<br />-Skript debugging<br />-Source Unterstützung<br />-Sicherheit<br />Seite-an-Seite<br />-SQL<br />-Server symbol<br />-Trace Punkte<br />-Thread<br />-Visualisierung<br />-Extensible Stylesheet Language Transformations (XSLT)-debugger|  
|64-Bit-Unterstützung|-64-Bit-Debuggen für verwalteten und systemeigenen Code, alle Sprachen<br />-X64 systemeigene Unterstützung|  
|Source Code Control (SCC)|-Grundlegende SCC-Integration. Siehe Hinweis 3.<br />-Tools und Optionen der Überprüfung|  
|Erweiterungen|-Nutzung von VSPackages und MEF-Komponenten|  
  
## <a name="notes"></a>Notizen  
  
#### <a name="1-data-tools"></a>1. Datentools  
 Die integrierte Shell enthält Datenbank-Entwicklungstools, wie die Unterstützung der Erweiterbarkeit und die vereinfachte **Projektmappen-Explorer**. Allerdings sind SQL Server Express, SQL Reporting und Crystal Reports in der integrierten Shell nicht enthalten.  
  
#### <a name="2-debugging-support"></a>2. Debugunterstützung  
 Die integrierte Shell enthält die gleichen Debugmodul, die in der Community-Version von Visual Studio enthalten ist. Debugmoduls enthält den allgemeinen Debugger für verwalteten Code sowie verwandten Funktionen, wie z. B. ausführen, anfügen, Haltepunkt festlegen, bearbeiten und Fortfahren sowie andere. Allerdings unterstützt Debugmoduls Debuggen von SQL Server-Datenbank nicht.  
  
 Obwohl Unterstützung für systemeigenes Debuggen in der grundlegenden Debuggerpaket enthalten ist, können nicht erweitert werden, um weitere Sprachen zu unterstützen.  
  
#### <a name="3-source-code-control-integration"></a>3. Integration der Quellcodeverwaltung  
 Die integrierte Shell stellt APIs bereit, für die Implementierung der Source Code Control (SCC) und für die Bereitstellung von des MSSCCI-basierte allgemeine Quellsteuerelement Integrationskomponenten.  
  
 SCC-Integration ist, zwar nicht die Pro-Edition von Visual Studio ein regelmäßiger wird die SCC-Integration in die integrierte Shell bereitgestellt.  
  
#### <a name="4-build-support"></a>4. Build-Unterstützung  
 Die integrierte Shell unterstützt Build. Sie können Informationen zu Builds, in dem [Referenz zu MSBuild-](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Die integrierte Shell nicht enthaltene Features  
 Im folgenden finden eine Liste der Funktionen, die nicht in der integrierten Shell enthalten sind:  
  
-   Klassen-Designer  
  
-   [PreEmptive Schutz - Dotfuscator](../ide/dotfuscator/index.md)  
  
-   Sprachfunktionen  
  
-   VSHost  
  
-   In der integrierten Shell sind keine Visual Studio-Sprachen oder ihre zugeordneten Projektvorlagen oder Projektelementvorlagen enthalten. Keine sprachspezifischen Implementierungen von anderen Funktionen sind enthalten, wird Visual Basic-Codeausschnitte.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Visual Studio-Übersicht](../Topic/Extending%20Visual%20Studio%20Overview.md)

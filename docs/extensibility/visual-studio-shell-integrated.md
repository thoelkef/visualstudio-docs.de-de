---
redirect_url: shell/visual-studio-shell-integrated
title: Visual Studio-Shell (integriert) | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b43e4ac1c8e40a9f4f378be42cc642767bee0777
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio-Shell (integriert)
Visual Studio integrierte Shell enthält die integrierten Entwicklungsumgebung (IDE), den Debugger und die Integration der quellcodeverwaltung. Keine Programmiersprache ist enthalten. Die integrierte Shell stellt jedoch ein Framework bereit, die Sie Programmiersprachen hinzufügen können.  
  
 Visual Studio integrierte Shell ist tatsächlich eine Kombination aus der Visual Studio isolated Shell plus eine zusätzliche Installation integrierte Shell bestimmte Komponenten einzuschließen.  Die integrierte Shell-Anwendung sollte sowohl die isolierte Shell verteilbares Paket enthalten [Microsoft Visual Studio Shell (isoliert) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022) sowie das verteilbare Paket für integrierte Shell von [Microsoft Visual Studio Shell (integriert) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Bevor Sie die verteilbaren Pakete von isolierten und integrierte Shell zugreifen können, werden Sie aufgefordert, eine kurze Umfrage auszufüllen.  Nach dem Ausfüllen der Umfrage, müssen Sie eine Verbindung zu Visual Studio-Seite mit verteilbare Paket Downloadlinks weitergeleitet.  Die Downloadlinks finden Sie bei nachfolgenden Besuchen der Visual Studio-Connect-Website unter der **Programme &#124; VISUAL STUDIO 2015 integriert und ISOLATED SHELL** Registerkarte.  
  
 Wenn Sie die integrierte Shell-Anwendung auf demselben Computer wie eine Vollversion von Visual Studio installieren, werden Ihre Anwendung Komponenten direkt in Visual Studio integriert werden.  
  
## <a name="features-in-the-integrated-shell"></a>Funktionen in die integrierte Shell  
  
|||  
|-|-|  
|Bereich „Funktionen“|Funktion|  
|Sprachenunterstützung|-Keine|  
|IDE|<ul><li>Einstellungen<br /><br /> <ul><li>Erstellen von Einstellungen</li><li>Importieren und Exportieren von Einstellungen</li><li>Einstellungen zum Zurücksetzen</li></ul></li><li>**Toolbox** Integration</li><li>**Aufgabenliste für die** Integration</li><li>Integration von Hilfe</li><li>**Optionen** (Dialogfeld)</li><li>Verwaltung von Schriftarten und Farben</li><li>**Ausgabe** Fenster</li><li>**Befehl** Fenster</li><li>Fensterverwaltung</li><li>Befehle, Menüs und Tastenkombinationen</li><li>Domänenspezifische Sprache (DSL) mit Common Language runtime</li></ul>|  
|Projektsystem und Projekttypen|-Lösungen und Projektmappenordner<br />-Konfigurations-Manager Lösung<br />-Management Element<br />-Lösungen Einzelprojekt- und mit mehreren Projekten<br />-Anwendungs-Designer (vereinfachte Projekteigenschaften)<br />-Webverweis hinzufügen<br />– Hinzufügen eines Dienstverweises<br />Einzelprojekt-<br />-Website Projekttypen<br />-Webanwendungsprojekte|  
|Build|-In der IDE benutzerdefinierte Buildschritte<br />-Vorkompilierung für den Schutz von geistigem Eigentum (IP)<br />-Codesignatur<br />     MSBuild|  
|Editor|-Codesuchdatenbank Tools (unified suchen, Datenquellendefinition, Inheritance)<br />-Code navigation<br />-IntelliSense<br />-SmartTags<br />-Umgestaltung<br />-Einrückung<br />-IntelliSense Filtern<br />-   **Code Definition** Fenster|  
|Designer|-Windows Presentation Foundation-Designer<br />-Windows Forms-Designer<br />-Web-Designer und HTML-Editor|  
|Daten|-   **Server-Explorer** (vereinfacht: nur Daten). Siehe Hinweis 1.<br />-   **Datenquellen** Fenster<br />-Sämtliche Datensteuerelemente<br />-XML-Editor<br />-Daten zu binden, um lokale Datenquelle (. MDF-Datei oder. MDB)<br />-Data-Bind Objekt<br />-Daten binden, Webdienst<br />-Daten zu binden, um den lokalen Datenbankserver<br />-Daten zu binden, um remote-Datenbankserver<br />-DDL Tools für die Remotedaten<br />-   **Server-Explorer** Erweiterbarkeit ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Beispiele)|  
|Debugger|– Lokales Debuggen. Siehe Hinweis 2.<br />-Verwaltetes Debuggen<br />– Lokales Debuggen<br />-Lokalen Prozess anfügen<br />-Remoteprozess zuordnen<br />-Anonymen Delegaten<br />-Anwendungsdomänen<br />-ASPX Debuggen<br />-Attribute<br />-Unterbrechen Sie während der Func-eval<br />-Haltepunkte<br />-Haltepunkt Einschränkungen<br />-Aufrufliste<br />-   **Befehl** Fenster<br />-Debuggen threadübergreifenden<br />-Datentipps<br />-Schnellansicht Daten<br />-Die Debuggerunterstützung für verwaltetes Debuggen (MDAs)<br />-Debugger Unterstützung für typweiterleitung<br />-DTEEvents Unterstützung für OTB<br />-"JMC" zugeordnetem<br />-Debugger AppID Test (DBGCLR)<br />-Debugger Profil<br />-Debuggers, Tools und Optionen<br />-Iterator debugging<br />-Auswertung von Ausdrücken zur Entwurfszeit<br />-C# Expression Evaluator<br />-Disassembly<br />-Bearbeiten und fortfahren<br />-Expression Evaluator Windows (Überwachung, "lokal", "Auto")<br />-Ausnahmen-Hilfe<br />-Ausnahmen<br />-Ausführung<br />– Generika<br />-Rechte Quelle abrufen<br />-Debuggen HPC-Cluster<br />-Integrierte Debuggen mehrerer Sprachen<br />-Interop-Debuggen<br />-Just-in-Time-Debuggen<br />– Lokales Debuggen<br />-Verwaltetes Debuggen<br />-Die manuelle Steuerung (Prozessfenster)<br />-Arbeitsspeicher<br />-MiniDump Unterstützung<br />-Module<br />-Debuggen Prozessen<br />-Systemeigenes Debuggen<br />– Neue Datenbankmodul-Debugunterstützung<br />-Optimierten Codedebuggen.<br />/ O-Windows-Filterung<br />-Verarbeiten Sie hosting für verwaltetes Debuggen<br />-Prozesse<br />-Schnellüberwachung<br />-Register<br />-Register Stapel<br />-Remotedebuggen<br />-Rückgabewerte<br />-Skript debugging<br />-Source Unterstützung<br />-Sicherheit<br />Seite-an-Seite<br />-SQL<br />-Server symbol<br />-Trace Punkte<br />-Thread<br />-Visualisierungen<br />-Extensible Stylesheet Language Transformations (XSLT)-debugger|  
|64-Bit-Unterstützung|-64-Bit-Debuggen für verwalteten und systemeigenen Code, alle Sprachen<br />-X64 systemeigene Unterstützung|  
|Quellcodeverwaltung (SCC)|-Grundlegende SCC-Integration. Siehe Hinweis 3.<br />-Tools und Optionen der Überprüfung|  
|Erweiterungen|-Nutzung von VSPackages und MEF-Komponenten|  
  
## <a name="notes"></a>Hinweise  
  
#### <a name="1-data-tools"></a>1. Data Tools  
 Die integrierte Shell enthält Datenbank Entwicklungstools wie z. B. Unterstützung für die Erweiterbarkeit von Daten und die vereinfachte **Projektmappen-Explorer**. Allerdings sind SQL Server Express, SQL Reporting und Crystal Reports in der integrierten Shell nicht enthalten.  
  
#### <a name="2-debugging-support"></a>2. Debugunterstützung  
 Die integrierte Shell enthält die gleichen Debugmodul konstruiert, die in der Community-Version von Visual Studio enthalten ist. Die Debugmodul enthält den allgemeinen Debugger für verwalteten Code, und auch verwandte Funktionen an, wie z. B. ausführen, anfügen, Haltepunkt festlegen, bearbeiten und Fortfahren sowie andere. Allerdings unterstützt der Debugmodul Debuggen von SQL Server-Datenbank nicht.  
  
 Obwohl Unterstützung für systemeigenes debugging im grundlegenden Debuggerpaket enthalten ist, können nicht erweitert, um zusätzliche Sprachen unterstützen.  
  
#### <a name="3-source-code-control-integration"></a>3. Integration der Quellcodeverwaltung  
 Die integrierte Shell stellt APIs bereit, zum Implementieren der quellcodeverwaltung (SCC) und für die Bereitstellung der MSSCCI-basierte allgemeine quellcodeverwaltung Integrationskomponenten.  
  
 SCC-Integration ist, zwar keine reguläre Funktion der Pro-Edition von Visual Studio wird in der integrierten Shell SCC-Integration bereitgestellt.  
  
#### <a name="4-build-support"></a>4. Build-Unterstützung  
 Die integrierte Shell unterstützt Build. Sie finden Informationen zu Builds in die [Referenz zu MSBuild-](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>In der integrierten Shell nicht enthaltene Funktionen  
 Im folgenden finden eine Liste der Funktionen, die nicht in der integrierten Shell enthalten sind:  
  
-   Klassen-Designer  
  
-   [PreEmptive Protection - Dotfuscator](../ide/dotfuscator/index.md)  
  
-   Sprachfunktionen  
  
-   VSHost  
  
-   Keine Visual Studio-Sprachen oder ihre zugeordneten Projektvorlagen oder Projektelementvorlagen, sind in der integrierten Shell enthalten. Keine sprachspezifischen-Implementierungen von anderen Funktionen sind enthalten, für Beispiel Visual Basic-Codeausschnitten.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
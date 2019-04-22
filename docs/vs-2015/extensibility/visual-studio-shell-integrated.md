---
title: Visual Studio-Shell (integriert) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 87c7b4faaf5aad737c8f7f8b653dbea03bc4de31
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59001893"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio-Shell (integriert)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Visual Studio integrierte Shell umfasst die integrierte Entwicklungsumgebung (IDE), Debugger und Integration der quellcodeverwaltung. Es ist keine Programmiersprache enthalten. Integrated Shell stellt jedoch ein Framework bereit, die Ihnen ermöglicht, Programmiersprachen hinzuzufügen.  
  
 Die Visual Studio integrierte Shell ist tatsächlich eine Kombination aus der Visual Studio isolierte Shell und eine weitere Installation der integrierten Shell bestimmte Komponenten einzuschließen.  Ihre Anwendung für die integrierte Shell von aufzunehmen sowohl das isolierte Shell redistributable Package vom [Microsoft Visual Studio Shell (isoliert) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022) sowie das integrierte Shell redistributable Package von [Microsoft Visual Studio Shell (integriert) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Bevor Sie die verteilbaren Pakete von isolated und die integrated Shell zugreifen können, werden Sie aufgefordert, einer kurzen Kundenumfrage auszufüllen.  Nach dem Ausfüllen der Umfrage, werden Sie auf eine Visual Studio Connect-Seite mit Links zum Herunterladen der verteilbaren Pakets weitergeleitet werden.  Die Download-Links finden Sie bei nachfolgenden Besuchen der Visual Studio Connect-Website unter der **Programme &#124; VISUAL STUDIO 2015 INTEGRATED und ISOLATED SHELL** Registerkarte.  
  
 Wenn Sie die integrierte Shell-Anwendung auf dem gleichen Computer wie die Vollversion von Visual Studio installieren, werden Ihrer Anwendung Komponenten direkt in Visual Studio integriert werden.  
  
## <a name="features-in-the-integrated-shell"></a>Funktionen in der integrierten Shell  
  
|||  
|-|-|  
|Bereich „Funktionen“|Feature|  
|Sprachenunterstützung|– None|  
|IDE|<ul><li>Einstellungen<br /><br /> <ul><li>Erstellen von Einstellungen</li><li>Einstellungen importieren und exportieren</li><li>Zurücksetzen von Einstellungen</li></ul></li><li>**Toolbox** Integration</li><li>**Aufgabenliste für** Integration</li><li>Integration von Hilfe</li><li>**Optionen** (Dialogfeld)</li><li>Verwaltung von Schriftarten und Farben</li><li>**Ausgabe** Fenster</li><li>**Befehl** Fenster</li><li>Fensterverwaltung</li><li>Befehle, Menüs und Tastenkombinationen</li><li>Domänenspezifische Sprache (DSL)-Laufzeit</li></ul>|  
|Projektsystem und Projekttypen|-Lösungen und Projektmappenordner<br />-Konfigurations-Manager Lösung<br />-Verwaltung<br />-Lösungen Single-Projekt und mit mehreren Projekten<br />-Anwendungs-Designer (vereinfachte Projekteigenschaften)<br />-Webverweis hinzufügen<br />– Hinzufügen eines Dienstverweises<br />-Single-Projekt<br />-Website Projekttypen<br />-Webanwendungsprojekte|  
|Build|– Benutzerdefinierte Buildschritte in IDE<br />– Vorkompilierung für den Schutz des geistigen Eigentums (IP)<br />: Signieren von code<br />     MSBuild|  
|Editor|-Code-Tools (einheitliche Suche, Quelldefinition, Vererbung) durchsuchen<br />: Navigation in code<br />-IntelliSense<br />-   SmartTags<br />-Refactoring<br />-Automatische Strukturierung<br />-IntelliSense Filterung<br />-   **Code Definition** Fenster|  
|Designer|– Windows Presentation Foundation-Designer<br />-Windows Forms-Designer<br />-Web-Designer und HTML-Editor|  
|Daten|-   **Server-Explorer** (vereinfacht: nur Daten). Siehe Hinweis 1.<br />-   **Datenquellen** Fenster<br />-Vollständiger Satz von Datensteuerelementen<br />-XML-Editor<br />-Daten zu binden, um die lokale Datenquelle (. MDF-Datei oder. MDB)<br />-Data-Bind-Objekt<br />-Daten zu binden, Webdienst<br />-Datenbindung mit lokalen Datenbankserver<br />-Datenbindung an remote-Datenbankserver<br />-DDL Tools für die Remotedaten<br />-   **Server-Explorer** Erweiterbarkeit ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Beispiele)|  
|Debugger|-Lokalen Debuggen. Siehe Hinweis 2.<br />– Verwaltetes Debuggen<br />– Lokales Debuggen<br />– An den lokalen Prozess anhängen.<br />-Fügen Sie dem Remoteprozess<br />-Anonymen Delegaten<br />-Anwendungsdomänen<br />-ASPX Debugging<br />-Attribute<br />-Wird unterbrochen Sie, während der eval-Funktion<br />-Haltepunkte<br />-Haltepunkt Einschränkungen<br />: Aufrufliste<br />-   **Befehl** Fenster<br />-Debuggen Cross-thread<br />-Datentipps<br />-Daten Schnellansicht<br />-Die Debuggerunterstützung für verwaltetes Debuggen (MDA)<br />-Debugger Unterstützung für typweiterleitung<br />-OTB DTEEvents Unterstützung<br />-JMC zugeordnetem<br />-Debugger AppID-Test (DBGCLR)<br />-Debugger Profil<br />-Debugger-Tools und Optionen<br />-Debug iterator<br />-Design-Time-ausdrucksauswertung<br />– C# Ausdrucksauswertung<br />-Disassembly<br />– Bearbeiten und fortfahren<br />-Expression Evaluator Windows (sehen Sie sich, "lokal", "Auto")<br />-Ausnahme-Hilfe<br />-Ausnahmen<br />-Execution<br />– Generics<br />– Abrufen der richtige Quelle<br />-Debuggen von HPC/Cluster<br />-Integrierte Debuggen mehrerer Sprachen<br />-InterOp-Debuggen<br />-Just-in-Time-Debuggen<br />– Lokales Debuggen<br />– Verwaltetes Debuggen<br />– Manuelle Steuerung (Fenster "Prozesse")<br />-Arbeitsspeicher<br />-MiniDump Unterstützung<br />-Module<br />-Debuggen mit mehreren Prozessen<br />-Systemeigenes Debuggen<br />– Neue Debug-Engine-Unterstützung<br />-Optimierten Codedebuggen<br />-Ausgabefenster filtern<br />– Verarbeiten Sie hosting für verwaltetes Debuggen<br />-Prozesse<br />-Schnellüberwachung<br />-Register<br />-Register im Stapel<br />-Remotedebuggen<br />-Rückgabewerte<br />: Debuggen von Skripts<br />-Source-dienstunterstützung<br />-Sicherheit<br />Seite-an-Seite<br />-   SQL<br />-Symbolserver<br />-Ablaufverfolgungspunkte<br />-Thread<br />-Visualisierungen<br />-Extensible Stylesheet Language Transformations (XSLT)-debugger|  
|64-Bit-Unterstützung|-64-Bit-Debuggen für verwalteten und systemeigenen Code, alle Sprachen<br />-native X64 unterstützen|  
|Quellcodeverwaltung (SCC)|-Einfache SCC-Integration. Siehe Hinweis 3.<br />-Tools und Optionen der Überprüfung|  
|Erweiterungen|– Nutzen Sie VSPackages und MEF-Komponenten|  
  
## <a name="notes"></a>Hinweise  
  
#### <a name="1-data-tools"></a>1. Data Tools  
 Integrated Shell umfasst Tools zur Datenbankentwicklung wie z. B. die Unterstützung der Erweiterbarkeit und die vereinfachte **Projektmappen-Explorer**. Allerdings sind SQL Server Express, SQL Reporting und Crystal Reports in der integrierten Shell nicht enthalten.  
  
#### <a name="2-debugging-support"></a>2. Debugunterstützung  
 Integrated Shell umfasst die gleiche Debug-Engine, die in der Community-Version von Visual Studio enthalten ist. Die Debug-Engine enthält den allgemeinen Debugger für verwalteten Code, und verwandten Funktionen, wie z. B. ausführen, anfügen, Haltepunkt festlegen, bearbeiten und fortfahren und andere. Allerdings unterstützt die Debug-Engine Debuggen von SQL Server-Datenbanken nicht.  
  
 Obwohl Unterstützung für systemeigenes Debuggen im basic Debuggerpaket enthalten ist, können nicht erweitert, um zusätzliche Sprachen zu unterstützen.  
  
#### <a name="3-source-code-control-integration"></a>3. Integration der quellcodeverwaltung  
 Die integrierte Shell stellt APIs bereit, zum Implementieren der quellcodeverwaltung (SCC) und für die Bereitstellung von Integrationskomponenten für die MSSCCI-basierte allgemeine Datenquellen-Steuerelement.  
  
 Obwohl-SCC-Integration nicht um eine reguläre Funktion der Pro-Edition von Visual Studio ist, wird-SCC-Integration in der integrierten Shell bereitgestellt.  
  
#### <a name="4-build-support"></a>4. Unterstützung für Build  
 Die integrierte Shell unterstützt Build. Sie erhalten Informationen zu Builds in die [MSBuild-Referenz](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>In der integrierten Shell nicht enthaltene Funktionen  
 Im folgenden finden eine Liste der Funktionen, die nicht in der integrierten Shell enthalten sind:  
  
-   Klassen-Designer  
  
-   PreEmptive Protection – Dotfuscator  
  
-   Sprachfunktionen  
  
-   VSHost  
  
-   Keine Visual Studio-Sprachen oder ihre zugeordneten Projektvorlagen oder Projektelementvorlagen, sind in der integrierten Shell enthalten. Keine sprachspezifische Implementierungen anderer Features sind enthalten, für das Beispiel Visual Basic-Codeausschnitte.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Visual Studio-Übersicht](http://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)
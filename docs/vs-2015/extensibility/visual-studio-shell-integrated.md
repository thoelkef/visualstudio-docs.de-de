---
title: Visual Studio Shell (integriert) | Microsoft-Dokumentation
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
ms.openlocfilehash: 6220afc2bdf75cc22529c65d5514f5f9e0766555
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919210"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (integriert)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Visual Studio Integrated Shell umfasst die Integration der IDE (integrierte Entwicklungsumgebung), des Debuggers und der Quellcodeverwaltung. Es ist keine Programmiersprache enthalten. Die integrierte Shell bietet jedoch ein Framework, das Ihnen das Hinzufügen von Programmiersprachen ermöglicht.  
  
 Die integrierte Shell von Visual Studio ist tatsächlich eine Kombination aus der isolierten Visual Studio-Shell sowie einer zusätzlichen Installation, die integrierte shellspezifische Komponenten umfasst.  Die integrierte Shellanwendung sollte sowohl das verteilbare verteilbare Shell-Paket als auch das integrierte Shell Redistributable Package enthalten, beides aus [Microsoft Visual Studio Shell Redistributable Packages](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).  
  
> [!NOTE]
> Bevor Sie auf die verteilbaren Pakete für die Isolated und die Integrated Shell zugreifen können, werden Sie gebeten, an einer kurzen Kundenumfrage teilzunehmen.  Nach dem Ausfüllen der Umfrage werden Sie auf eine Visual Studio Connect-Seite mit Downloadlinks für die verteilbaren Pakete geleitet.  Die Download Links finden Sie auf den nachfolgenden Besuchen auf der Visual Studio Connect-Website **unter &#124; Programme Visual Studio 2015 Integrated and isolierte Shell** (Registerkarte).  
  
 Wenn Sie die integrierte Shell-Anwendung auf demselben Computer wie eine Vollversion von Visual Studio installieren, werden die Komponenten der Anwendung direkt in Visual Studio integriert.  
  
## <a name="features-in-the-integrated-shell"></a>Funktionen in der integrierten Shell  
  
|||  
|-|-|  
|Bereich „Funktionen“|Feature|  
|Sprachenunterstützung|-None|  
|-IDE|<ul><li>Einstellungen<br /><br /> <ul><li>Erstellen von Einstellungen</li><li>Importieren und Exportieren von Einstellungen</li><li>Zurücksetzen von Einstellungen</li></ul></li><li>**Toolbox** -Integration</li><li>**Aufgabenliste** Integration</li><li>Hilfe Integration</li><li>Dialogfeld " **Optionen** "</li><li>Verwaltung von Schriftarten und Farben</li><li>**Ausgabe** Fenster</li><li>**Befehls** Fenster</li><li>Fensterverwaltung</li><li>Befehle, Menüs und Tastenkombinationen</li><li>Laufzeit der domänenspezifischen Sprache (DSL)</li></ul>|  
|Projekt System-und Projekttypen|-Lösungen und Projektmappenordner<br />-Projektmappenkonfigurations-Manager<br />-Element Verwaltung<br />-Lösungen mit einem Projekt und mehreren Projekten<br />-Anwendungs-Designer (vereinfachte Projekteigenschaften)<br />-Webverweis hinzufügen<br />-Dienstverweis hinzufügen<br />-Einzelprojekt<br />-Website Projekttypen<br />-Webanwendungs Projekte|  
|Erstellen|-Benutzerdefinierte Buildschritte in der IDE<br />-Vorkompilierung für den Schutz geistigen Eigentums (IP)<br />-Code Signatur<br />     MSBuild|  
|-Editor|-Tools zum Durchsuchen von Code (vereinheitlichte Suche, Quell Definition, Vererbung)<br />-Code Navigation<br />-IntelliSense<br />-Smarttags<br />-Refactoring<br />-Schöne Auflistung<br />-IntelliSense-Filterung<br />Fenster " **Code Definition** -   "|  
|-Designer|-Windows Presentation Foundation-Designer<br />-Windows Forms-Designer<br />-Web-Designer und HTML-Editor|  
|importieren|-   **Server-Explorer** (vereinfacht: nur Daten). Siehe Hinweis 1.<br />Fenster " **Datenquellen** -   "<br />-Vollständiger Satz von Daten Steuerelementen<br />-XML-Editor<br />-Datenbindung an lokale Datenquelle (. MDF oder. Erfasst<br />-Datenbindung an Objekt<br />-Datenbindung an Webdienst<br />-Datenbindung an den lokalen Datenbankserver<br />-Datenbindung an Remote Datenbankserver<br />-DDL-Tools für Remote Daten<br />-   **Server-Explorer** Erweiterbarkeit ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Beispiele)|  
|Debugger|-Lokales Debuggen. Siehe Hinweis 2.<br />-Verwaltetes Debugging<br />-Lokales Debuggen<br />-An lokalen Prozess anfügen<br />-An Remote Prozess anhängen<br />-Anonymer Delegat<br />-Anwendungs Domänen<br />-ASPX-Debuggen<br />-Attribute<br />-Unterbrechung bei Func-eval<br />-Breakpoints<br />-Breakpoint-Einschränkungen<br />-Callstack<br />-   **Befehls** Fenster<br />-Thread übergreifendes Debuggen<br />-Daten Tipps<br />-Daten Schnellansicht<br />-Debugger-Unterstützung für Assistenten für verwaltetes Debuggen (MDAs)<br />-Debugger-Unterstützung für die Typweiterleitung<br />-DTEEvents-Unterstützung für OTB<br />-JMC-Stepper<br />-Debugger-AppID-Test (DbgCLR)<br />-Debugger-Profil<br />-Debugger-Tools und-Optionen<br />-Debugging-Iterator<br />-Ausdrucks Auswertung zur Entwurfszeit<br />- C# Ausdrucks Auswertung<br />-Disassembly<br />-Bearbeiten und fortfahren<br />-Ausdrucks auswerterfenster (Watch, Locals, Auto)<br />-Exception-Hilfsprogramm<br />-Ausnahmen<br />-Ausführung<br />– Generics<br />-Die richtige Quelle wird erhalten.<br />-HPC-/clusterdebugging<br />-Integriertes mehrsprachiges Debuggen<br />-Interop-Debuggen<br />-Just-in-Time-Debuggen<br />-Lokales Debuggen<br />-Verwaltetes Debugging<br />-Manuelles Steuerelement (Prozessfenster)<br />- Arbeitsspeicher<br />-Minidump-Unterstützung<br />-Module<br />-Debuggen mit mehreren Prozessen<br />-Natives Debuggen<br />-Neue Debug-Engine-Unterstützung<br />-Optimiertes Code Debugging<br />-Ausgabe Windows-Filterung<br />-Prozess Hosting für verwaltetes Debuggen<br />-Prozesse<br />-Schnell Überwachung<br />-Register<br />-Register im Stapel<br />-Remote Debuggen<br />-Rückgabewerte<br />-Skript Debugging<br />-Quell Dienst Unterstützung<br />-Sicherheit<br />-Seite-an-Seite<br />-SQL<br />-Symbol Server<br />-Ablauf Verfolgungs Punkte<br />-Thread<br />-Visualisierungen<br />-Extensible Stylesheet Language Transformations (XSLT)-Debugger|  
|64-Bit-Unterstützung|-64-Bit-Debuggen für verwalteten und nativen Code, alle Sprachen<br />-x64 Native Unterstützung|  
|Quell Code Verwaltung (SCC)|-Grundlegende SCC-Integration. Siehe Hinweis 3.<br />-Tools und Options Überprüfung|  
|Erweiterungen|-Verwenden von VSPackages und MEF-Komponenten|  
  
## <a name="notes"></a>Hinweise  
  
#### <a name="1-data-tools"></a>1. Daten Tools  
 Die integrierte Shell umfasst Daten Bank Entwicklungs Tools wie die Unterstützung der Daten Erweiterbarkeit und die vereinfachte **Projektmappen-Explorer**. Allerdings sind SQL Server Express-, SQL Reporting-und Crystal-Berichte nicht in der integrierten Shell enthalten.  
  
#### <a name="2-debugging-support"></a>2. Debuggingunterstützung  
 Die integrierte Shell enthält dieselbe Debug-Engine, die in der Community-Version von Visual Studio enthalten ist. Das Debugmodul enthält den allgemeinen Debugger für verwalteten Code sowie verwandte Funktionen wie "ausführen", "anfügen", "Haltepunkt festlegen", "Bearbeiten und Fortfahren" und andere. Die Debug-Engine unterstützt jedoch nicht das Debuggen von SQL Server Datenbanken.  
  
 Obwohl die Unterstützung für natives Debuggen im Standard Debugger-Paket enthalten ist, können Sie es nicht erweitern, um zusätzliche Sprachen zu unterstützen.  
  
#### <a name="3-source-code-control-integration"></a>3. Integration der Quell Code Verwaltung  
 Die integrierte Shell stellt APIs zum Implementieren der Quell Code Verwaltung (Source Code Control, SCC) und zum Bereitstellen der MSSCCI-basierten allgemeinen Quell Code Verwaltungs Komponenten bereit.  
  
 Obwohl die SCC-Integration kein reguläres Feature der Pro-Edition von Visual Studio ist, wird die SCC-Integration in der integrierten Shell bereitgestellt.  
  
#### <a name="4-build-support"></a>4. Buildunterstützung  
 Die integrierte Shell bietet Buildunterstützung. Informationen zu Builds finden Sie in der [MSBuild-Referenz](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Features, die nicht in der integrierten Shell enthalten sind  
 Im folgenden finden Sie eine Liste der Funktionen, die nicht in der integrierten Shell enthalten sind:  
  
- Klassen-Designer  
  
- PreEmptive Protection – Dotfuscator  
  
- Sprachfunktionen  
  
- VSHost  
  
- In der integrierten Shell sind keine Visual Studio-Sprachen oder die zugehörigen Projektvorlagen oder Projekt Element Vorlagen enthalten. Es sind keine sprachspezifischen Implementierungen anderer Features enthalten, z. b. Visual Basic Code Ausschnitte.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Visual Studio (Übersicht)](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)

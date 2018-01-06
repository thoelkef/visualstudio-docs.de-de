---
title: Visual Studio isolierte Shell | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e80b947b2d4d20692e0abceae0ffa36e64f2b0df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio isolierte Shell
Die Visual Studio isolated Shell können Sie eigenständige Anwendungen zu erstellen, die Seite-an-Seite ausführen können mit anderen Versionen von Visual Studio. Es ist in erster Linie um spezielle Tools zu hosten, die mithilfe von Visual Studio-Dienste können jedoch auch benutzerdefinierte Darstellung aufweisen verwendet und branding. Visual Studio-Funktionen und Menügruppen-Befehl können problemlos aktiviert oder deaktiviert werden. Anwendungstitel, Symbole und Begrüßungsbildschirme sind vollständig anpassbar. Eine Liste der anpassbare Features, finden Sie unter [anpassen Isolated Shell](customizing-the-isolated-shell.md).  
  
 Um mit einer isolierten Shell-Projekt arbeiten, müssen Sie das Visual Studio SDK installieren. Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../installing-the-visual-studio-sdk.md).  
  
 Um eine isolierte Shell-Anwendung erstellen, beginnen Sie mit einem Visual Studio Shell Isolated-Projekt. Dieses Projekt enthält alles, was Sie benötigen zum Entwickeln und Testen Ihre eigenen isolierten Shell-Anwendung. Wenn Sie bereit sind, das Setup-Programm zu schreiben, die Ihre Anwendung bereitgestellt wird, benötigen Sie die isolierte Shell verteilbares Paket [Microsoft Visual Studio Shell (isoliert) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Bevor Sie das verteilbare Paket für isolierte Shell zugreifen können, werden Sie aufgefordert, eine kurze Umfrage auszufüllen.  Nach dem Ausfüllen der Umfrage, müssen Sie eine Verbindung zu Visual Studio-Seite mit verteilbare Paket Downloadlinks weitergeleitet.  Die Downloadlinks finden Sie bei nachfolgenden Besuchen der Visual Studio-Connect-Website unter der **Programme &#124; VISUAL STUDIO 2015 integriert und ISOLATED SHELL** Registerkarte.  
  
> [!NOTE]
>  Weitere Informationen zum Bereitstellen einer isolierten Shell-basierten Anwendung finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Arbeiten mit isolierte shell  
 Eine Visual Studio isolated Shell-Anwendung verfügt über Vollzugriff auf Visual Studio-Dienste und unterstützt spezielle Anpassung und branding. Es gibt mehrere Möglichkeiten, die Sie eine isolierten Shell-Anwendung anpassen können:  
  
-   VSPackages und Managed Extensibility Framework (MEF) Komponenten können auf eine isolierten Shell-Anwendung erweitern, wie Sie in eine andere Visual Studio-Erweiterung verwenden möchten. Weitere Informationen finden Sie unter [erweitern Isolated Shell](extending-the-isolated-shell.md).  
  
-   Um Visual Studio-Funktionen und Menü Befehlsgruppen verfügbar oder nicht verfügbar zu machen, aktualisieren Sie die VSCT-Datei im Projekt Benutzer Benutzeroberfläche (UI) der Anwendung.  
  
-   So entfernen Sie **Optionen** Seiten oder andere Visual Studio-Shell-Komponenten der Anwendung, die .pkgundef-Datei der Anwendung aktualisiert.  
  
-   Aktualisieren Sie die PKGDEF-Datei der Anwendung, um andere Aspekte der Darstellung oder Verhalten der Shell zu ändern.  
  
-   Einige Aspekte der Shell können auch angegeben werden, wenn die Anwendung gestartet wird. Aktualisieren Sie zu diesem Zweck den Parameter im Aufruf basierend auf den Eintrag Ausgangspunkt der appenvstub.dll.  
  
 Weitere Informationen zu den verschiedenen Elemente, die Sie anpassen können, finden Sie unter [Elemente der isolierte Shell](elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Standardfunktionen der isolierte Shell  
 Die folgenden Funktionen sind für alle Editionen von Visual Studio standard.  
  
|Funktionskategorie|Funktion|  
|----------------------|-------------|  
|IDE-Funktionen|Import/Export-Einstellungen<br /><br /> Installer für Werkzeugkasten-Steuerelement<br /><br /> Aufgabenliste und Fehlerliste<br /><br /> Ausgabefenster<br /><br /> Startseite<br /><br /> Eigenschaftenfenster<br /><br /> Werkzeugkasten<br /><br /> Projektmappen-Explorer<br /><br /> Lesezeichenfenster<br /><br /> Klassenansicht<br /><br /> Objektkatalog<br /><br /> Befehlsfenster<br /><br /> Dokumentgliederung<br /><br /> Ressourcenansicht<br /><br /> Externe Tools<br /><br /> Windows Communication Foundation (WCF) Hinzufügen eines Dienstverweises<br /><br /> Language Integrated Query (LINQ)-Unterstützung|  
|Editor-Designer|Codesuchdatenbank Tools (unified suchen, Datenquellendefinition, Inheritance)<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Codeausschnitt-Manager<br /><br /> Codeausschnitte<br /><br /> Umgestaltung<br /><br /> Einrückung<br /><br /> IntelliSense-Filtern<br /><br /> Codedefinitionsfenster<br /><br /> Anwendungs-Designer<br /><br /> Windows Forms-Designer<br /><br /> Windows Presentation Foundation (WPF) Designer|  
|Debuggen|C#-Ausdrucksauswerter<br /><br /> Lokales Debuggen<br /><br /> Verwaltetes Debuggen<br /><br /> Bearbeiten und Fortfahren<br /><br /> Threadübergreifende Debuggen<br /><br /> Visualisierungen<br /><br /> DataTips<br /><br /> Systemeigenes Debuggen<br /><br /> Skriptdebuggen<br /><br /> Interop-Debuggen<br /><br /> Debuggen von Just-in-Time (JIT)<br /><br /> Debuggen von Prozessen<br /><br /> XSLT-debugging<br /><br /> Fügen an lokale Prozess an<br /><br /> Ablaufverfolgungspunkte<br /><br /> Haltepunkt-Einschränkungen|  
|Daten|Server-Explorer (vereinfacht - nur Daten)<br /><br /> Binden von Daten mit lokalen Daten (. MDF-Datei oder. MDB)<br /><br /> Datenbindung an Objekt<br /><br /> Datenbindung an den Webdienst<br /><br /> Sämtliche Datensteuerelemente<br /><br /> XML-editor<br /><br /> Binden von Daten zu lokalen Datenbankserver<br /><br /> Datenquellenfenster|  
|Web|HTML-Editor<br /><br /> Webbrowser<br /><br /> Web Forms-Designer<br /><br /> Website-Projekt<br /><br /> Web-Anwendungsprojekt|  
|Erweiterungen|VSPackages und MEF-Komponenten nutzt|  
  
## <a name="see-also"></a>Siehe auch  
 [Shell (Isolated oder Integrated)](shell-isolated-or-integrated.md)
---
title: Visual Studio Shell Isolated | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 35
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: d6925bbb3fa432c098f62d223b1c1a7478ecca23
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-isolated-shell"></a>Visual Studio Shell Isolated
Visual Studio isolated Shell können Sie eigenständige Anwendung zu erstellen, Side-by-Side mit anderen Versionen von Visual Studio. Es ist in erster Linie um spezielle Tools zu hosten, die mithilfe von Visual Studio-Dienste können jedoch auch benutzerdefinierte Darstellung aufweisen verwendet und branding. Visual Studio-Funktionen und Befehl Menügruppen können leicht aktiviert oder deaktiviert werden. Anwendungstitel, Symbole und Begrüßungsbildschirme sind vollständig anpassbar. Eine Liste der anpassbaren Features, finden Sie unter [Anpassen der isolierte Shell](../extensibility/customizing-the-isolated-shell.md).  
  
 Um mit einem isolierte Shell-Projekt arbeiten, müssen Sie das Visual Studio SDK installieren. Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installation von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Um eine isolierte Shell-Anwendung erstellen, beginnen Sie mit einem Visual Studio Shell Isolated Projekt. Dieses Projekt enthält alles, was Sie benötigen, entwickeln und Testen Ihre eigene isolierte Shell-Anwendung. Wenn Sie bereit sind, das Setup-Programm zu schreiben, die Ihre Anwendung bereitgestellt wird, benötigen Sie das isolierte Shell redistributable Package vom [Microsoft Visual Studio Shell (isoliert) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Bevor Sie das isolierte Shell redistributable Package zugreifen können, werden Sie aufgefordert, eine kurze Umfrage ausfüllen.  Nach dem Ausfüllen der Umfrage teilnehmen, werden Sie zu Visual Studio Connect Downloadlinks verteilbare Paket weitergeleitet.  Sie finden die Downloadlinks bei nachfolgenden Besuchen der Visual Studio Connect-Website unter der **Programme | VISUAL STUDIO 2015 integriert und ISOLIERTE SHELL** Registerkarte.  
  
> [!NOTE]
>  Weitere Informationen zum Bereitstellen einer isolierte Shell-basierten Anwendung finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung für isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Arbeiten mit der isolierte shell  
 Eine Visual Studio isolated Shell-Anwendung hat vollen Zugriff auf Visual Studio-Dienste und unterstützt spezielle anpassen und branding. Es gibt mehrere Methoden, die Sie eine isolierte Shell-Anwendung anpassen können:  
  
-   Sie können jedoch VSPackages und das Managed Extensibility Framework (MEF)-Komponenten verwenden, eine isolierte Shell-Anwendung zu erweitern, wie Sie in anderen Visual Studio-Erweiterung verwenden möchten. Weitere Informationen finden Sie unter [erweitern die isolierte Shell](../extensibility/extending-the-isolated-shell.md).  
  
-   Damit Visual Studio-Funktionen und Menügruppen Befehl verfügbar sind, aktualisieren Sie die VSCT-Datei im Projekt Benutzer Benutzeroberfläche (UI) der Anwendung.  
  
-   So entfernen Sie **Optionen** Seiten oder andere Visual Studio-Shell-Komponenten von der Anwendung die .pkgundef-Datei der Anwendung aktualisiert.  
  
-   Aktualisieren Sie die PKGDEF-Datei der Anwendung, um andere Aspekte der Darstellung oder Verhalten der Shell zu ändern.  
  
-   Einige Aspekte der Shell können auch angegeben werden, wenn die Anwendung gestartet wird. Dazu aktualisieren Sie die Parameter im Aufruf an den Eintrag Ausgangspunkt der appenvstub.dll.  
  
 Weitere Informationen zu den verschiedenen Elementen, die Sie anpassen können, finden Sie unter [Elemente der isolierte Shell](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Standardfunktionen der isolierte Shell  
 Die folgenden Funktionen sind für alle Editionen von Visual Studio standard.  
  
|Funktionskategorie|Funktion|  
|----------------------|-------------|  
|IDE-Features|Importieren und Exportieren von Einstellungen<br /><br /> Installer für Werkzeugkasten-Steuerelement<br /><br /> Aufgabenliste & Fehlerliste<br /><br /> Ausgabefenster<br /><br /> Startseite<br /><br /> Eigenschaftenfenster<br /><br /> Werkzeugkasten<br /><br /> Projektmappen-Explorer<br /><br /> Lesezeichenfenster<br /><br /> Klassenansicht<br /><br /> Objektkatalog<br /><br /> Befehlsfenster<br /><br /> Dokumentgliederung<br /><br /> Ressourcenansicht<br /><br /> Externe Tools<br /><br /> Windows Communication Foundation (WCF) Hinzufügen eines Dienstverweises<br /><br /> Language Integrated Query (LINQ)-Unterstützung|  
|Editor-Designer|Tools (unified suchen, Datenquellendefinition, Vererbung) Durchsuchen von Code<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Codeausschnitt-Manager<br /><br /> Codeausschnitte<br /><br /> Umgestaltung<br /><br /> Einrückung<br /><br /> IntelliSense-Filtern<br /><br /> Codedefinitionsfenster<br /><br /> Anwendungs-Designer<br /><br /> Windows Forms-Designer<br /><br /> Windows Presentation Foundation (WPF)-Designer|  
|Debuggen|C#-Ausdrucksauswerter<br /><br /> Lokales Debuggen<br /><br /> Verwaltetes Debuggen<br /><br /> Bearbeiten und Fortfahren<br /><br /> Threadübergreifende Debuggen<br /><br /> Visualisierungen<br /><br /> DataTips<br /><br /> Systemeigenes Debuggen<br /><br /> Debuggen von Skripts<br /><br /> Interop-Debuggen<br /><br /> Just-in-Time (JIT)-Debuggen<br /><br /> Mehrere Prozesse debuggen.<br /><br /> XSLT-Debuggen<br /><br /> An lokalen Prozess anfügen<br /><br /> Ablaufverfolgungspunkte<br /><br /> Haltepunkt-Einschränkungen|  
|Daten|Server-Explorer (vereinfacht - nur Daten)<br /><br /> Bindet Daten an lokale Daten (. MDF-Datei oder. MDB)<br /><br /> Daten binden an Objekt<br /><br /> Daten binden an Web service<br /><br /> Vollständigen Satz von Steuerelementen von<br /><br /> XML-editor<br /><br /> Bindet Daten an den lokalen Datenbankserver<br /><br /> Datenquellenfenster|  
|Web|HTML-Editor<br /><br /> Webbrowser<br /><br /> Web Forms-Designer<br /><br /> Website-Projekt<br /><br /> Webanwendungsprojekt|  
|Erweiterungen|Nutzt VSPackages und MEF-Komponenten|  
  
## <a name="see-also"></a>Siehe auch  
 [Shell (isoliert oder integriert)](../extensibility/shell-isolated-or-integrated.md)

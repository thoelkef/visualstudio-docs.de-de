---
title: Visual Studio Isolated Shell | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59ecd079b7e95d86ab85eb9e5e36fcf938f99f58
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959516"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Visual Studio isolierte Shell können Sie eigenständige Anwendungen zu erstellen, die Seite-an-Seite ausführen, können mit anderen Versionen von Visual Studio. Es ist in erster Linie, um spezielle Tools zu hosten, die Visual Studio-Dienste verwenden können, jedoch auch benutzerdefinierte Darstellung aufweisen, verwendet und ein branding. Visual Studio-Features und Menügruppen-Befehl können problemlos auf aktiviert oder deaktiviert werden. Anwendungstitel, Symbole und Begrüßungsbildschirme sind vollständig anpassbar. Eine Liste der anpassbaren Features, finden Sie unter [Anpassen der Isolated Shell](../extensibility/customizing-the-isolated-shell.md).  
  
 Um mit einer isolierten Shell-Projekt arbeiten, müssen Sie das Visual Studio SDK installieren. Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Um einer isolierten Shell-Anwendung zu erstellen, beginnen Sie mit einem isolierten Visual Studio Shell-Projekt. Dieses Projekt enthält alles, was Sie benötigen zum Entwickeln und Testen Ihre eigene isolierte Shell-Anwendung. Wenn Sie bereit sind, das Setup-Programm zu schreiben, die Ihre Anwendung bereitgestellt wird, muss man das isolierte Shell redistributable Package vom [Microsoft Visual Studio Shell (isoliert) Redistributable Package](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Bevor Sie das verteilbare Paket von isolated Shell zugreifen können, werden Sie aufgefordert, einer kurzen Kundenumfrage auszufüllen.  Nach dem Ausfüllen der Umfrage, werden Sie auf eine Visual Studio Connect-Seite mit Links zum Herunterladen der verteilbaren Pakets weitergeleitet werden.  Die Download-Links finden Sie bei nachfolgenden Besuchen der Visual Studio Connect-Website unter der **Programme &#124; VISUAL STUDIO 2015 INTEGRATED und ISOLATED SHELL** Registerkarte.  
  
> [!NOTE]
>  Weitere Informationen zum Bereitstellen einer isolierten Shell-basierten Anwendung finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Verwendung der isolated Shells  
 Eine Visual Studio isolated Shell-Anwendung hat vollen Zugriff auf Visual Studio-Diensten und unterstützt spezielle Anpassungen und branding. Es gibt mehrere Möglichkeiten, die Sie eine isolierten Shell-Anwendung anpassen können:  
  
- VSPackages und Managed Extensibility Framework (MEF) Komponenten können auf um eine isolierten Shell-Anwendung zu erweitern, wie Sie in eine andere Visual Studio-Erweiterung verwenden möchten. Weitere Informationen finden Sie unter [Erweitern der Isolated Shell](../extensibility/extending-the-isolated-shell.md).  
  
- Um Visual Studio-Funktionen und Menü Befehlsgruppen verfügbar oder nicht verfügbar zu machen, aktualisieren Sie die VSCT-Datei in das Benutzerprojekt-Benutzeroberfläche (UI) der Anwendung.  
  
- So entfernen Sie **Optionen** Seiten oder andere Visual Studio-Shell-Komponenten von der Anwendung, die pkgundef-Datei der Anwendung zu aktualisieren.  
  
- Um andere Aspekte der Darstellung oder Verhalten der Shell zu ändern, aktualisieren Sie die PKGDEF-Datei der Anwendung.  
  
- Einige Aspekte der Shell können auch angegeben werden, wenn die Anwendung gestartet wird. Aktualisieren Sie die Parameter im Aufruf an den Start-Einstiegspunkt, der die appenvstub.dll, zu diesem Zweck.  
  
  Weitere Informationen zu den verschiedenen Elementen, die Sie anpassen können, finden Sie unter [Elemente der Isolated Shell](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Standardfunktionen der Isolated Shell  
 Die folgenden Features sind für alle Editionen von Visual Studio standard.  
  
|Funktionskategorie|Feature|  
|----------------------|-------------|  
|IDE-Features|Importieren und Exportieren von Einstellungen<br /><br /> Installer für Toolbox-Steuerelement<br /><br /> Aufgabenliste und Fehlerliste<br /><br /> Ausgabefenster<br /><br /> Startseite<br /><br /> Eigenschaftenfenster<br /><br /> Werkzeugkasten<br /><br /> Projektmappen-Explorer<br /><br /> Lesezeichenfenster<br /><br /> Klassenansicht<br /><br /> Objektkatalog<br /><br /> Befehlsfenster<br /><br /> Dokumentgliederung<br /><br /> Ressourcenansicht<br /><br /> Externes Tool<br /><br /> Windows Communication Foundation (WCF) Dienstverweis hinzufügen<br /><br /> Language Integrated Query (LINQ)-Unterstützung|  
|Designer/Editor|Code-Tools (einheitliche Suche, Quelldefinition, Vererbung) durchsuchen<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Codeausschnitt-Manager<br /><br /> Codeausschnitte<br /><br /> Umgestaltung<br /><br /> Automatische Strukturierung<br /><br /> IntelliSense-Filter<br /><br /> Codedefinitionsfenster<br /><br /> Anwendungs-Designer<br /><br /> Windows Forms-Designer<br /><br /> Windows Presentation Foundation (WPF) Designer|  
|Debuggen|C#-Ausdrucksauswertung<br /><br /> Lokales Debuggen<br /><br /> Verwaltetes Debuggen<br /><br /> Bearbeiten und Fortfahren<br /><br /> Debuggen von Threads<br /><br /> Visualisierungen<br /><br /> DataTips<br /><br /> Systemeigenes Debuggen<br /><br /> Debuggen von Skripts<br /><br /> Interop-Debuggen<br /><br /> Debuggen von Just-in-Time (JIT)<br /><br /> Debuggen mit mehreren Prozessen<br /><br /> Debuggen von XSLT-Code<br /><br /> An den lokalen Prozess anhängen<br /><br /> Ablaufverfolgungspunkte<br /><br /> Haltepunkt-Einschränkungen|  
|Daten|Server-Explorer (vereinfacht – nur Daten)<br /><br /> Datenbindung an lokalen Daten (. MDF-Datei oder. MDB)<br /><br /> Datenbindung an Objekt<br /><br /> Datenbindung an den Webdienst<br /><br /> Breites Spektrum an Datensteuerelemente<br /><br /> XML-Editor<br /><br /> Datenbindung an den lokalen Datenbankserver<br /><br /> Datenquellenfenster|  
|Web|HTML-Editor<br /><br /> Webbrowser<br /><br /> Web Forms-Designer<br /><br /> Website-Projekt<br /><br /> Webanwendungsprojekt|  
|Erweiterungen|VSPackages und MEF-Komponenten nutzt|  
  
## <a name="see-also"></a>Siehe auch  
 [Shell (Isolated oder Integrated)](../extensibility/shell-isolated-or-integrated.md)

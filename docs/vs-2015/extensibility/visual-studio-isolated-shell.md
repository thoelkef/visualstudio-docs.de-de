---
title: Isolierte Visual Studio-Shell | Microsoft-Dokumentation
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
ms.openlocfilehash: 01917b9e78ee6129f09811ca2dc3e18c149c06f6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850392"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio Shell (isoliert)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von Visual Studio Isolated Shell können Sie eigenständige Anwendungen erstellen, die parallel mit anderen Versionen von Visual Studio ausgeführt werden können. Sie wird in erster Linie zum Hosten spezieller Tools verwendet, die Visual Studio-Dienste verwenden können, aber auch über eine angepasste Darstellung und ein eigenes Branding verfügen. Visual Studio-Funktionen und Menübefehls Gruppen können problemlos aktiviert und deaktiviert werden. Anwendungs Titel, Anwendungs Symbole und Begrüßungs Bildschirme sind vollständig anpassbar. Eine Liste der anpassbaren Features finden Sie unter [Anpassen der isolierten Shell](../extensibility/customizing-the-isolated-shell.md).  
  
 Wenn Sie mit einem isolierten shellprojekt arbeiten möchten, müssen Sie das Visual Studio SDK installieren. Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Wenn Sie eine isolierte Shell-Anwendung erstellen möchten, beginnen Sie mit einem von Visual Studio Shell isolierten Projekt. Dieses Projekt enthält alles, was Sie zum entwickeln und Testen Ihrer eigenen isolierten Shellanwendung benötigen. Wenn Sie bereit sind, das Setup Programm zu schreiben, mit dem Ihre Anwendung bereitgestellt wird, müssen Sie das isolierte verteilbare Shell-Paket aus [Microsoft Visual Studio Shell (isoliert) verteilbaren Pakets](https://docs.microsoft.com/collaborate/connect-redirect?ProgramID=8963&InvitationID=VS15-2R69-RB8J)erhalten.  
  
> [!NOTE]
> Bevor Sie auf das verteilbare Paket für isolierte Shell zugreifen können, werden Sie aufgefordert, eine kurze Kundenumfrage auszufüllen.  Nach dem Ausfüllen der Umfrage werden Sie auf eine Visual Studio Connect-Seite mit Downloadlinks für die verteilbaren Pakete geleitet.  Die Download Links finden Sie auf den nachfolgenden Besuchen auf der Visual Studio Connect-Website **unter &#124; Programme Visual Studio 2015 Integrated and isolierte Shell** (Registerkarte).  
  
> [!NOTE]
> Weitere Informationen zum Bereitstellen einer isolierten Shell-basierten Anwendung finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Arbeiten mit der isolierten Shell  
 Eine isolierte Visual Studio-Shellanwendung hat vollen Zugriff auf Visual Studio-Dienste und unterstützt besondere Anpassungen und Branding. Es gibt mehrere Möglichkeiten, wie Sie eine isolierte Shellanwendung anpassen können:  
  
- Sie können VSPackages und Managed Extensibility Framework Komponenten Komponenten (MEF) verwenden, um eine isolierte Shellanwendung so zu erweitern, wie Sie Sie in jeder anderen Visual Studio-Erweiterung verwenden würden. Weitere Informationen finden Sie unter [Erweitern der isolierten Shell](../extensibility/extending-the-isolated-shell.md).  
  
- Um Visual Studio-Funktionen und Menübefehls Gruppen verfügbar zu machen oder nicht verfügbar zu machen, aktualisieren Sie die vsct-Datei im Benutzeroberflächen Projekt (UI) der Anwendung.  
  
- Aktualisieren Sie die pkgundef-Datei der Anwendung, um **options** Seiten oder andere Visual Studio Shell-Komponenten aus der Anwendung zu entfernen.  
  
- Um andere Aspekte der Darstellung oder des Verhaltens der Shell zu ändern, aktualisieren Sie die pkgdef-Datei der Anwendung.  
  
- Einige Aspekte der Shell können auch beim Starten der Anwendung angegeben werden. Aktualisieren Sie zu diesem Zweck die Parameter im-Befehl auf den Start Einstiegspunkt der Datei appenvstub. dll.  
  
  Weitere Informationen zu den verschiedenen Elementen, die Sie anpassen können, finden Sie unter [Elemente der isolierten Shell](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Standard Features der isolierten Shell  
 Die folgenden Features sind standardmäßig für alle Editionen von Visual Studio.  
  
|Funktionskategorie|Feature|  
|----------------------|-------------|  
|IDE-Features|Importieren und Exportieren von Einstellungen<br /><br /> Toolbox-Steuerelement<br /><br /> Aufgabenliste & Fehlerliste<br /><br /> Ausgabefenster<br /><br /> Startseite<br /><br /> Eigenschaftenfenster<br /><br /> Toolbox<br /><br /> Projektmappen-Explorer<br /><br /> Lesezeichenfenster<br /><br /> Klassenansicht<br /><br /> Objektkatalog<br /><br /> Befehlsfenster<br /><br /> Dokumentgliederung.<br /><br /> Ressourcenansicht<br /><br /> Externes Tool<br /><br /> Windows Communication Foundation (WCF) Dienstverweis hinzufügen<br /><br /> LINQ-Unterstützung (Language Integrated Query)|  
|Editor/Designer|Tools zum Durchsuchen von Code (vereinheitlichte Suche, Quell Definition, Vererbung)<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Codeausschnitt-Manager<br /><br /> -Codeausschnitte<br /><br /> Umgestaltung<br /><br /> Schöne Auflistung<br /><br /> IntelliSense-Filterung<br /><br /> Codedefinitionsfenster<br /><br /> Anwendungs-Designer<br /><br /> Windows Forms-Designer<br /><br /> Windows Presentation Foundation (WPF)-Designer|  
|Debugging|C#Ausdrucks Auswertung<br /><br /> Lokales Debugging<br /><br /> Verwaltetes Debugging<br /><br /> "Bearbeiten und Fortfahren"<br /><br /> Thread übergreifendes Debuggen<br /><br /> Visualisierungen<br /><br /> DataTips<br /><br /> Natives Debuggen<br /><br /> Debuggen von Skripts<br /><br /> Interop-Debugging<br /><br /> Just-in-time (JIT)-Debuggen<br /><br /> Debuggen mit mehreren Prozessen<br /><br /> Debuggen von XSLT-Code<br /><br /> An lokalen Prozess anhängen<br /><br /> Ablaufverfolgungspunkte<br /><br /> Haltepunkt Einschränkungen|  
|importieren|Server-Explorer (nur vereinfachte Daten)<br /><br /> Datenbindung an lokale Daten (. MDF oder. Erfasst<br /><br /> Datenbindung an Objekt<br /><br /> Datenbindung an Webdienst<br /><br /> Vollständiger Satz von Daten Steuerelementen<br /><br /> XML-Editor<br /><br /> Datenbindung an den lokalen Datenbankserver<br /><br /> Datenquellenfenster|  
|Web|HTML-Editor<br /><br /> Webbrowser<br /><br /> Web Forms-Designer<br /><br /> Websiteprojekt<br /><br /> Webanwendungsprojekt|  
|Erweiterungen|Nutzung von VSPackages und MEF-Komponenten|  
  
## <a name="see-also"></a>Siehe auch  
 [Shell (Isolated oder Integrated)](../extensibility/shell-isolated-or-integrated.md)

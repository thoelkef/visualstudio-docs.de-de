---
title: "Erstellen einer eigenen Startseite | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Startseite erstellen"
  - "benutzerdefinierte Startseite"
  - "Startseite anpassen"
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# Erstellen einer eigenen Startseite
Sie können eine benutzerdefinierte Startseite mithilfe der Projektvorlage für Startseiten oder auf Grundlage einer leeren Startseite erstellen.  
  
 Der XAML\-Designer bietet möglicherweise aufgrund von Abhängigkeiten vom Visual Studio\-Anwendungsmodell keine genauen optischen Darstellungen von benutzerdefinierten Startseiten.  
  
## Verwenden der Projektvorlage  
 Mit der Projektvorlage für Startseiten wird ein Startseitenprojekt erstellt. Dabei handelt es sich um eine vollständige Kopie der Visual Studio\-Startseite. Sie können die Startseite dann entsprechend Ihren Anforderungen bearbeiten.  
  
#### So erstellen Sie eine benutzerdefinierte Startseite mithilfe der Projektvorlage für Startseiten  
  
1.  Laden Sie die [Projektvorlage für Startseiten](http://go.microsoft.com/fwlink/?LinkId=186204) aus der Visual Studio Gallery herunter, und installieren Sie sie.  
  
    > [!WARNING]
    >  Bislang wurde die Projektvorlage für Startseiten von Visual Studio 2010 nicht aktualisiert. Informationen zum Aktualisieren dieser Vorlage finden Sie unter [Gewusst wie: Aktualisieren einer benutzerdefinierten Visual Studio\-Startseite](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2.  Nachdem Sie die Vorlage installiert haben, erstellen Sie auf deren Grundlage ein neues Startseitenprojekt.  
  
3.  Erweitern Sie im linken Bereich des Dialogfelds "Neues Projekt" unter **Installierte Vorlagen** den Knoten **Andere Projekttypen**, und klicken Sie dann auf **Erweiterungen**.  
  
4.  Klicken Sie im mittleren Bereich auf **Benutzerdefinierte Startseite**, geben Sie einen Namen für das Projekt an, und klicken Sie auf **OK**.  
  
     Visual Studio erstellt ein Startseitenprojekt. Dabei handelt es sich um eine vollständige Kopie der Visual Studio\-Startseite.  
  
5.  Öffnen Sie im **Projektmappen\-Explorer** die Datei **StartPage.xaml**.  
  
6.  Bearbeiten Sie "StartPage.xaml".  
  
     Sie können Ihre Arbeit anzeigen, indem Sie F5 drücken. Dadurch wird eine experimentelle Visual Studio\-Instanz mit der installierten benutzerdefinierten Startseite geöffnet.  
  
## Erstellen einer leeren Startseite  
 Am einfachsten erstellen Sie eine leere Startseite mithilfe der Projektvorlage für Startseiten, aus der Sie den Inhalt entfernt haben.  
  
#### So erstellen Sie eine leere Startseite mithilfe der Projektvorlage für Startseiten  
  
1.  Erstellen Sie ein Startseitenprojekt mithilfe der Projektvorlage für Startseiten, wie in der vorherigen Vorgehensweise beschrieben.  
  
2.  Öffnen Sie "StartPage.xaml".  
  
3.  Entfernen Sie den gesamten Seiteninhalt, und behalten Sie nur die äußeren XML\-Elemente und das enthaltende <xref:System.Windows.Controls.Grid>\-Element bei, sodass die XAML\-Datei folgendem Beispiel ähnelt.  
  
     [!code-xml[BlankStartPage#01](../misc/codesnippet/Xaml/creating-your-own-start-page_1.xaml)]  
  
4.  Entfernen Sie alle Hilfsdateien, die Sie nicht benötigen.  
  
     Behalten Sie für die Bereitstellung die VSIX\-Datei und die PKGDEF\-Datei.  
  
 Alternativ können Sie eine leere Startseite erstellen, indem Sie eine XAML\-Datei mit der korrekten, von Visual Studio zu erkennenden Tagstruktur erstellen. Sie können dann Markup und CodeBehind hinzufügen, um die gewünschte Darstellung und die erforderlichen Funktionen zu erhalten. Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md).  
  
## Testen und Anwenden der benutzerdefinierten Startseite  
 Legen Sie zum Ausführen der benutzerdefinierten Startseite die primäre Instanz erst fest, wenn Sie sicher sind, dass kein Absturz erfolgt. Wenn Sie die benutzerdefinierte Startseite getestet haben, können Sie sie für Ihr System übernehmen. Dazu führen Sie die letzten drei Schritte dieser Vorgehensweise in der primären Visual Studio\-Instanz aus.  
  
#### So testen Sie eine benutzerdefinierte Startseite  
  
1.  Drücken Sie F5.  
  
     Die experimentelle Visual Studio\-Instanz wird mit der neuen installierten Startseite geöffnet, sie ist aber nicht ausgewählt.  
  
2.  Klicken Sie in der experimentellen Visual Studio\-Instanz im Menü **Extras** auf **Optionen**.  
  
3.  Wählen Sie im Dialogfeld **Optionen** unter **Umgebung** die Option **Start** aus. Wählen Sie dann in der Liste **Startseite anpassen** die XAML\-Datei aus, und klicken Sie auf **OK**.  
  
4.  Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
     Die Arbeitsstartseite wird angezeigt. Sie müssen die experimentelle Instanz schließen, alle geänderten Dateien erneut kopieren und dann die experimentelle Instanz erneut öffnen, damit die Änderungen angezeigt werden.  
  
 Sie können die benutzerdefinierte Startseite freigeben. Dazu laden Sie die VSIX\-Datei aus dem Verzeichnis "bin\\debug" in die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847)\-Website bzw. eine andere Website oder eine Intranetfreigabe. Weitere Informationen finden Sie unter [Bereitstellen von benutzerdefinierte Startseiten](../extensibility/deploying-custom-start-pages.md).  
  
## Siehe auch  
 [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
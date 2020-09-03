---
title: Erstellen einer eigenen Start Seite | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: jillfra
ms.openlocfilehash: fba7f1e0801b6f977d47b13af025538f5d2fe031
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850981"
---
# <a name="creating-your-own-start-page"></a>Erstellen einer eigenen Startseite
Sie können eine benutzerdefinierte Startseite mithilfe der Projektvorlage für Startseiten oder auf Grundlage einer leeren Startseite erstellen.  
  
 Der XAML-Designer bietet möglicherweise aufgrund von Abhängigkeiten vom Visual Studio-Anwendungsmodell keine genauen optischen Darstellungen von benutzerdefinierten Startseiten.  
  
## <a name="using-the-project-template"></a>Verwenden der Projektvorlage  
 Mit der Projektvorlage für Startseiten wird ein Startseitenprojekt erstellt. Dabei handelt es sich um eine vollständige Kopie der Visual Studio-Startseite. Sie können die Startseite dann entsprechend Ihren Anforderungen bearbeiten.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>So erstellen Sie eine benutzerdefinierte Startseite mithilfe der Projektvorlage für Startseiten  
  
1. Laden Sie die [Projektvorlage für Startseiten](https://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) aus der Visual Studio Gallery herunter, und installieren Sie sie.  
  
    > [!WARNING]
    > Bislang wurde die Projektvorlage für Startseiten von Visual Studio 2010 nicht aktualisiert. Weitere Informationen zum Aktualisieren dieser Vorlage finden Sie unter Gewusst [wie: Aktualisieren einer benutzerdefinierten Visual Studio-Start Seite](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2. Nachdem Sie die Vorlage installiert haben, erstellen Sie auf deren Grundlage ein neues Startseitenprojekt.  
  
3. Erweitern Sie im linken Bereich des Dialogfelds "Neues Projekt" unter **Installierte Vorlagen**den Knoten **Andere Projekttypen** , und klicken Sie dann auf **Erweiterungen**.  
  
4. Klicken Sie im mittleren Bereich auf **Benutzerdefinierte Startseite**, geben Sie einen Namen für das Projekt an, und klicken Sie auf **OK**.  
  
     Visual Studio erstellt ein Startseitenprojekt. Dabei handelt es sich um eine vollständige Kopie der Visual Studio-Startseite.  
  
5. Öffnen Sie im **Projektmappen-Explorer**die Datei **StartPage.xaml**.  
  
6. Bearbeiten Sie "StartPage.xaml".  
  
     Sie können Ihre Arbeit anzeigen, indem Sie F5 drücken. Dadurch wird eine experimentelle Visual Studio-Instanz mit der installierten benutzerdefinierten Startseite geöffnet.  
  
## <a name="creating-a-blank-start-page"></a>Erstellen einer leeren Startseite  
 Am einfachsten erstellen Sie eine leere Startseite mithilfe der Projektvorlage für Startseiten, aus der Sie den Inhalt entfernt haben.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>So erstellen Sie eine leere Startseite mithilfe der Projektvorlage für Startseiten  
  
1. Erstellen Sie ein Startseitenprojekt mithilfe der Projektvorlage für Startseiten, wie in der vorherigen Vorgehensweise beschrieben.  
  
2. Öffnen Sie "StartPage.xaml".  
  
3. Entfernen Sie den gesamten Seiteninhalt, und behalten Sie nur die äußeren XML-Elemente und das enthaltende <xref:System.Windows.Controls.Grid>-Element bei, sodass die XAML-Datei folgendem Beispiel ähnelt.  
  
   ```xaml
      <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
            mc:Ignorable="d" 
                d:DesignHeight="600" d:DesignWidth="800">
       <Grid>
           <!--Add content here.-->
       </Grid>
   </Grid>
   ```
      
4. Entfernen Sie alle Hilfsdateien, die Sie nicht benötigen.  
  
    Behalten Sie für die Bereitstellung die VSIX-Datei und die PKGDEF-Datei.  
  
   Alternativ können Sie eine leere Startseite erstellen, indem Sie eine XAML-Datei mit der korrekten, von Visual Studio zu erkennenden Tagstruktur erstellen. Sie können dann Markup und CodeBehind hinzufügen, um die gewünschte Darstellung und die erforderlichen Funktionen zu erhalten. Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten Start Seite](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testen und Anwenden der benutzerdefinierten Startseite  
 Legen Sie zum Ausführen der benutzerdefinierten Startseite die primäre Instanz erst fest, wenn Sie sicher sind, dass kein Absturz erfolgt. Wenn Sie die benutzerdefinierte Startseite getestet haben, können Sie sie für Ihr System übernehmen. Dazu führen Sie die letzten drei Schritte dieser Vorgehensweise in der primären Visual Studio-Instanz aus.  
  
#### <a name="to-test-a-custom-start-page"></a>So testen Sie eine benutzerdefinierte Startseite  
  
1. Drücken Sie F5.  
  
    Die experimentelle Visual Studio-Instanz wird mit der neuen installierten Startseite geöffnet, sie ist aber nicht ausgewählt.  
  
2. Klicken Sie in der experimentellen Visual Studio-Instanz im Menü **Extras** auf **Optionen**.  
  
3. Wählen Sie im Dialogfeld **Optionen** unter **Umgebung**die Option **Start**aus. Wählen Sie dann in der Liste **Startseite anpassen** die XAML-Datei aus, und klicken Sie auf **OK**.  
  
4. Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
    Die Arbeitsstartseite wird angezeigt. Sie müssen die experimentelle Instanz schließen, alle geänderten Dateien erneut kopieren und dann die experimentelle Instanz erneut öffnen, damit die Änderungen angezeigt werden.  
  
   Sie können Ihre benutzerdefinierte Start Seite freigeben, indem Sie die vsix-Datei aus dem Verzeichnis "bin\debug" auf die [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Website oder eine andere Website oder eine Intranetfreigabe hochladen. Weitere Informationen finden Sie unter [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anpassen der Start Seite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)

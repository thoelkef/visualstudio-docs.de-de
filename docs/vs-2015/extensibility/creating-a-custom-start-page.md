---
title: Erstellen einer benutzerdefinierten Startseite | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e7fbc9f18a668cbe3738ab3c8dd734ddadd8ce08
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947210"
---
# <a name="creating-a-custom-start-page"></a>Erstellen einer benutzerdefinierten Startseite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine benutzerdefinierte Startseite mithilfe der Projektvorlage "Startseite", wie in beschrieben erstellen können [Startseiten](../misc/creating-your-own-start-page.md), können Sie manuell die Schritte in diesem Dokument erstellen.  
  
## <a name="creating-a-blank-start-page"></a>Erstellen einer leeren Startseite  
 Stellen Sie zunächst eine leere Startseite erstellen Sie eine XAML-Datei, die eine Tagstruktur, die Visual Studio erkennt. Anschließend fügen Sie Markup und CodeBehind zu erzeugen, die Darstellung und Funktionalität, die Sie möchten.  
  
#### <a name="to-create-a-blank-start-page"></a>Um eine leere Startseite erstellen  
  
1.  Erstellen eines neuen Projekts vom Typ **WPF-Anwendung** (**Visual c# / Windows-Desktop**.  
  
2.  Fügen Sie einen Verweis auf `Microsoft.VisualStudio.Shell.14.0` hinzu.  
  
3.  Öffnen Sie die XAML-Datei im XML-Editor, und Ändern der obersten Ebene \<Fenster >-Element ein \<UserControl >-Element ohne die Namespacedeklarationen zu entfernen.  
  
4.  Entfernen Sie die `x:Class` Deklaration aus dem Element oberster Ebene. Dadurch wird den XAML-Inhalt mit der Visual Studio-Toolfenster, das die Startseite hostet kompatibel.  
  
5.  Fügen Sie die folgenden Namespacedeklarationen der obersten Ebene \<UserControl > Element.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Diese Namespaces können Sie die Visual Studio-Befehle, Steuerelementen und Einstellungen für Benutzeroberfläche zugreifen. Weitere Informationen finden Sie unter [Hinzufügen von Visual Studio-Befehle auf einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     Das folgende Beispiel zeigt das Markup in der XAML-Datei für eine leere Startseite. Alle benutzerdefinierter Inhalt gesendet werden sollen, in der inneren <xref:System.Windows.Controls.Grid> Element.  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  Hinzufügen von Steuerelementen auf ein leeres \<UserControl >-Element So füllen Sie die benutzerdefinierte Startseite. Weitere Informationen zum Hinzufügen von Funktionen, die in Visual Studio spezifisch sind, finden Sie unter [Hinzufügen von Visual Studio-Befehle auf einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testen und Anwenden der benutzerdefinierten Startseite  
 Legen Sie die primäre Instanz von Visual Studio der benutzerdefinierten Startseite ausgeführt werden soll, bis Sie sicherstellen, dass Visual Studio kein Absturz erfolgt nicht. Testen Sie es stattdessen in der experimentellen Instanz ein.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>So testen Sie eine manuell erstellte benutzerdefinierte Startseite  
  
1.  Kopieren der XAML-Datei und alle unterstützenden Textdateien oder Markup-Dateien, zu der **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\**  Ordner.  
  
2.  Wenn Ihre Startseite verweist keine Steuerelemente oder Typen in Assemblys, die von Visual Studio nicht installiert sind, kopieren Sie die Assemblys, und fügen Sie sie in _Visual Studio-Installationsordner_**\Common7\IDE\ "Privateassemblies"\\**.  
  
3.  Geben Sie an einer Visual Studio-Eingabeaufforderung **Devenv/rootsuffix Exp** um eine experimentelle Instanz von Visual Studio zu öffnen.  
  
4.  Wechseln Sie in der experimentellen Instanz zu den **Extras / Optionen / Umgebung / Start** Seite, und wählen Sie die XAML-Datei aus der **Customize Start Page** Dropdownliste.  
  
5.  Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
     Der benutzerdefinierten Startseite sollte angezeigt werden. Wenn Sie Dateien ändern möchten, müssen Sie die experimentelle Instanz schließen, nehmen Sie die Änderungen, kopieren und fügen Sie die geänderten Dateien und öffnen Sie erneut die experimentelle Instanz um die Änderungen anzuzeigen.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Zum Anwenden die benutzerdefinierten Startseite in der primären Instanz von Visual Studio  
  
-   Verwenden, nachdem Sie Ihre Startseite getestet und fand es stabil sein, die **Customize Start Page** option die **Optionen** im Dialogfeld für die Auswahl als Startseite in der primären Instanz von Visual Studio  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefinierten XAML zur Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Hinzufügen eines Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)   
 [Hinzufügen von Visual Studio-Befehlen zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Bereitstellen von benutzerdefinierten Startseiten](../extensibility/deploying-custom-start-pages.md)

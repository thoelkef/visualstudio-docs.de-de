---
title: Erstellen einer benutzerdefinierten Startseite | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 18
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
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 2902ac3b5cd4fd038bdaf277a8390d5eb9e96b28
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-custom-start-page"></a>Erstellen einer benutzerdefinierten Startseite
Sie können eine benutzerdefinierte Startseite erstellen, indem Sie die Schritte in diesem Dokument.  
  
## <a name="creating-a-blank-start-page"></a>Erstellen einer leeren Startseite  
 Stellen Sie zunächst eine leere Startseite durch Erstellen einer XAML-Datei mit einem Tag-Struktur, die Visual Studio erkennt. Dann fügen Sie Markup und Code-Behind zu erzeugen, die Darstellung und die gewünschten Funktionen.  
  
#### <a name="to-create-a-blank-start-page"></a>Erstellen Sie eine leere Seite starten  
  
1.  Erstellen eines neuen Projekts vom Typ **WPF-Anwendung** (**Visual c# / Windows-Desktop**.  
  
2.  Fügen Sie einen Verweis auf `Microsoft.VisualStudio.Shell.14.0` hinzu.  
  
3.  Die XAML-Datei im XML-Editor öffnen und Ändern der obersten Ebene \<Fenster > Element eine \<UserControl > Element ohne die Namespacedeklarationen entfernen.  
  
4.  Entfernen Sie die `x:Class` Deklaration aus dem Element der obersten Ebene. Dadurch wird den XAML-Inhalt mit der Visual Studio-Toolfenster, das die Startseite hostet kompatibel.  
  
5.  Fügen Sie die folgenden Namespacedeklarationen auf der obersten Ebene \<UserControl > Element.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Diese Namespaces können Sie die Visual Studio-Befehle, Steuerelemente und Benutzeroberflächeneinstellungen zugreifen. Weitere Informationen finden Sie unter [Visual Studio-Befehle hinzufügen, eine Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     Das folgende Beispiel zeigt das Markup in der XAML-Datei für eine leere Seite starten. Alle benutzerdefinierter Inhalt gesendet werden soll, in der inneren <xref:System.Windows.Controls.Grid>Element.</xref:System.Windows.Controls.Grid>  
  
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
  
6.  Hinzufügen von Steuerelementen zu einem leeren \<UserControl > Element So füllen Sie die benutzerdefinierte Startseite. Informationen zum Hinzufügen von Funktionen, die Visual Studio-spezifisch ist, finden Sie unter [Visual Studio-Befehle hinzufügen, eine Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testen und Anwenden der benutzerdefinierten Startseite  
 Stellen Sie keine primäre Instanz von Visual Studio die benutzerdefinierte Startseite ausgeführt werden soll, bis Sie sicherstellen, dass sie nicht Visual Studio abstürzt. Testen Sie es stattdessen in der experimentellen Instanz.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>So testen Sie eine manuell erstellte benutzerdefinierte Startseite  
  
1.  Kopieren Sie die XAML-Datei, und alle unterstützenden Textdateien oder Markup-Dateien, zu der **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\ ** Ordner.  
  
2.  Wenn Ihre Startseite verweist keine Steuerelemente oder Typen in Assemblys, die von Visual Studio nicht installiert sind, kopieren Sie die Assemblys, und fügen Sie sie in *Visual Studio-Installationsordner***\Common7\IDE\PrivateAssemblies\\**.  
  
3.  Geben Sie an einer Visual Studio-Eingabeaufforderungsfenster **Devenv/rootsuffix Exp** um eine experimentelle Instanz von Visual Studio zu öffnen.  
  
4.  Wechseln Sie in der experimentellen Instanz, zu der **Extras / Optionen / Umgebung / Start** Seite und wählen Sie die XAML-Datei aus der **Startseite anpassen** Dropdown-Liste.  
  
5.  Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
     Eine benutzerdefinierte Startseite angezeigt werden sollen. Wenn Sie Dateien ändern möchten, müssen Sie schließen Sie die experimentelle Instanz ändern, kopieren und fügen Sie die geänderten Dateien und öffnen Sie dann erneut die experimentelle Instanz um die Änderungen anzuzeigen.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Zum Anwenden die benutzerdefinierten Startseite in der primären Instanz von Visual Studio  
  
-   Verwenden, nachdem Sie Ihre Startseite getestet und ermittelt, dass stabil sein, die **Startseite anpassen** -Option in der **Optionen** Dialogfeld als Startseite in der primären Instanz von Visual Studio auswählen  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Hinzufügen des Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)   
 [Hinzufügen von Visual Studio-Befehle zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen einer Startseite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Bereitstellen von benutzerdefinierte Startseiten](../extensibility/deploying-custom-start-pages.md)

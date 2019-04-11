---
title: 'Schritt 1: Erstellen eines Windows Forms-Anwendungsprojekts'
ms.date: 03/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f529d737816406b3a4f6aa9921a8dc6b902d2fb
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647361"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Schritt 1: Erstellen eines Windows Forms-Anwendungsprojekts

Beim Erstellen einer Bildanzeige erstellen Sie im ersten Schritt ein Windows Forms-Anwendungsprojekt.

 > [!TIP]
 > ![Videolink](../data-tools/media/playvideo.gif) Videos zu diesem Thema finden Sie unter [Tutorial 1: Create a picture viewer in Visual Basic – Video 1 (Tutorial 1: Erstellen eines Bildanzeigeprogramms in Visual Basic – Video 1)](http://go.microsoft.com/fwlink/?LinkId=205209) und [Tutorial 1: Create a picture viewer in C# – Video 1 (Tutorial 1: Erstellen eines Bildanzeigeprogramms in C# – Video 1)](http://go.microsoft.com/fwlink/?LinkId=205199). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Das Dialogfeld sollte wie folgt aussehen.

     ![Dialogfeld „Neues Projekt“](../ide/media/newprojectdialogcallouts.png)<br/>
*Dialogfeld **Neues Projekt***

2. Wählen Sie im Dialogfenster **Neues Projekt** im linken Bereich **Visual C#** oder **Visual Basic** aus.

3. Wählen Sie in der Vorlagenliste **Windows Forms-App (.NET Framework)** aus. Geben Sie dem neuen Formular den Namen **PictureViewer**, und wählen Sie dann die Schaltfläche **OK** aus.

    >[!NOTE]
    >Wenn Ihnen die Vorlage **Windows Forms-App (.NET Framework)** nicht angezeigt wird, verwenden Sie den Visual Studio-Installer, um die Workload **.NET Desktop-Entwicklung** zu installieren.<br/><br/>![Die Workload „.NET Desktopentwicklung“ im Visual Studio-Installer](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Weitere Informationen finden Sie im Artikel [Installieren von Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Öffnen von Visual Studio 2019

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   ![Anzeigen des Fensters „Neues Projekt erstellen“](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld den Begriff *Windows Forms* ein. Wählen Sie anschließend in der Liste der Sprachen **Visual Basic** und dann aus der Liste der Plattformen **Windows** aus. 

   Nachdem Sie die Sprach- und Plattformfilter angewendet haben, wählen Sie die Vorlage **Windows Forms-App (.NET Framework)** und dann **Weiter** aus.

   ![Screenshot: Auswählen der Visual Basic-Vorlage für die Windows Forms-App (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Wenn Sie die **Windows Forms-App (.NET Framework)** nicht sehen, können Sie sie aus dem Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus.
   >
   > ![Link „Weitere Tools und Features installieren“ aus der Meldung „Sie finden nicht, wonach Sie suchen“ im Fenster „Neues Projekt erstellen“](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Wählen Sie anschließend im Visual Studio-Installer die Workload **.NET Desktopentwicklung** aus.
   > 
   > ![Die Workload „.NET Core“ im Visual Studio-Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Wählen Sie anschließend die Schaltfläche **Ändern** im Visual Studio-Installer aus. Möglicherweise werden Sie aufgefordert, Ihre Arbeit zu speichern; wenn dies der Fall ist, führen Sie das aus. Wählen Sie als Nächstes **Weiter** aus, um die Workload zu installieren. 

1. Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname** den Begriff *PictureViewer* ein. Wählen Sie anschließend **Erstellen** aus.

::: moniker-end

Visual Studio erstellt eine Projektmappe für das Programm. Eine Projektmappe fungiert als Container für alle Projekte und Dateien, die vom Programm benötigt werden. Diese Begriffe werden später ausführlicher in diesem Tutorials erläutert.

## <a name="about-the-windows-forms-application-project"></a>Übersicht über das Windows Forms-Anwendungsprojekt

1. Die Entwicklungsumgebung enthält drei Fenster: ein Hauptfenster, den **Projektmappen-Explorer** und das Fenster **Eigenschaften**.

     Wenn eines der Fenster fehlt, stellen Sie das Standardfensterlayout wieder her. Wählen Sie dazu in der Menüleiste die Optionen **Fenster** > **Fensterlayout zurücksetzen** aus. Sie können Fenster auch mit den Menübefehlen anzeigen. Klicken Sie in der Menüleiste auf **Anzeigen** > **Eigenschaftenfenster** oder auf **Projektmappen-Explorer**. Wenn andere Fenster geöffnet sind, schließen Sie diese mit der Schaltfläche **Schließen** (x), die sich jeweils in der rechten oberen Ecke befindet.

    ::: moniker range="vs-2017"

    - **Hauptfenster** In diesem Fenster führen Sie die meisten Schritte aus, z. B. Arbeiten mit Formularen oder Bearbeiten von Code. Im Fenster wird ein Formular im **Formular-Editor** angezeigt. Oben im Fenster werden die Registerkarte **Startseite** und die Registerkarte **Form1.cs [Entwurf]** angezeigt. (In Visual Basic endet der Registerkartenname mit *.vb* und nicht mit *.cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    - **Hauptfenster** In diesem Fenster führen Sie die meisten Schritte aus, z. B. Arbeiten mit Formularen oder Bearbeiten von Code. Im Fenster wird ein Formular im **Formular-Editor** angezeigt.

    ::: moniker-end

    - Fenster **Projektmappen-Explorer**: In diesem Fenster können Sie alle Elemente in der Projektmappe anzeigen und dorthin navigieren. Wenn Sie eine Datei auswählen, ändert sich der Inhalt im Fenster **Eigenschaften**. Wenn Sie eine Codedatei (die in Visual C# mit *.cs* und in Visual Basic mit *.vb* endet) öffnen, wird die Codedatei oder ein Designer für die Codedatei angezeigt. Ein Designer ist eine visuelle Oberfläche, der Sie Steuerelemente wie Schaltflächen und Listen hinzufügen können. Für Visual Studio-Formulare wird der Designer als **Windows Forms-Designer** bezeichnet.

    - **Eigenschaftenfenster:** In diesem Fenster können Sie die Eigenschaften von Elementen ändern, die Sie in den anderen Fenstern auswählen. Wenn Sie z. B. Form1 auswählen, können Sie den Titel ändern, indem Sie die Eigenschaft **Text** festlegen, und die Hintergrundfarbe ändern, indem Sie die Eigenschaft **Hintergrundfarbe** festlegen.

    > [!NOTE]
    > In der obersten Zeile im **Projektmappen-Explorer** wird **Projektmappe ‚PictureViewer‘ (1 Projekt)** angezeigt, was bedeutet, dass Visual Studio eine Projektmappe für Sie erstellt hat. Eine Projektmappe kann mehr als ein Projekt enthalten. Vorerst arbeiten Sie jedoch mit Projektmappen, die nur ein Projekt enthalten.

1. Klicken Sie in der Menüleiste auf **Datei** > **Alle speichern**.

     Wählen Sie alternativ die Schaltfläche **Alle speichern** auf der Symbolleiste aus, die in der folgenden Abbildung dargestellt ist.

     Schaltfläche ![Alle speichern](../ide/media/express_iconsaveall.png) in der Symbolleiste<br/>
     *Symbolleistenschaltfläche **Alle speichern***

     Visual Studio fügt automatisch den Ordnernamen und den Projektnamen ein und speichert das Projekt dann im Projektordner.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Den nächsten Schritt des Tutorials finden Sie unter [Schritt 2: Ausführen des Programms](../ide/step-2-run-your-program.md).

- Um zum Übersichtsthema zurückzukehren, beachten Sie [Tutorial 1: Create a picture viewer (Tutorial 1: Erstellen eines Bildanzeigeprogramms)](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Siehe auch

- [Creating a new Windows Form (Erstellen eines neuen Windows-Formulars)](/dotnet/framework/winforms/creating-a-new-windows-form/)
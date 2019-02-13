---
title: 'Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bab093c450a7913ea0f1d3e94b6d04e287c6c539
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911077"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular
In diesem Schritt fügen Sie Ihrem Formular die Komponenten <xref:System.Windows.Forms.OpenFileDialog> und <xref:System.Windows.Forms.ColorDialog> hinzu, damit Ihr Programm Bilddateien öffnen und eine Hintergrundfarbe auswählen kann.

 Eine Komponente ist in gewisser Hinsicht mit einem Steuerelement vergleichbar. Zum Hinzufügen einer Komponente in Ihr Formular verwenden Sie die **Toolbox**, und Sie legen die Eigenschaften im **Eigenschaftenfenster** fest. Aber im Gegensatz zu einem Steuerelement wird dem Formular beim Hinzufügen einer Komponente kein für den Benutzer sichtbares Element hinzugefügt. Stattdessen stellt die Komponente bestimmte Verhalten bereit, die Sie mit Code auslösen können. Es handelt sich dabei um eine Komponente, die das Dialogfeld **Datei öffnen** anzeigt.

 ![Videolink](../data-tools/media/playvideo.gif) Videos zu diesem Thema finden Sie unter [Tutorial 1: Create a picture viewer in Visual Basic – Video 3 (Tutorial 1: Erstellen eines Bildanzeigeprogramms in Visual Basic – Video 3)](http://go.microsoft.com/fwlink/?LinkId=205213) und [Tutorial 1: Create a picture viewer in C# – Video 3 (Tutorial 1: Erstellen eines Bildanzeigeprogramms in C# – Video 3)](http://go.microsoft.com/fwlink/?LinkId=205202). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.

## <a name="to-add-dialog-components-to-your-form"></a>So fügen Sie dem Formular Dialogfeldkomponenten hinzu

1.  Wählen Sie den **Windows Forms-Designer** (**Form1.cs [Entwurf]** oder **Form1.vb [Entwurf]**) aus, und öffnen Sie dann die Gruppe **Dialogfelder** in der **Toolbox**.

    > [!NOTE]
    >  Die Gruppe **Dialogfelder** in der **Toolbox** verfügt über Komponenten zum Öffnen vieler nützlicher Dialogfelder, die z.B. zum Öffnen und Speichern von Dateien, Durchsuchen von Ordnern und Auswählen von Schriftarten und Farben verwendet werden können. Sie verwenden in diesem Projekt zwei Dialogfeldkomponenten: OpenFileDialog und ColorDialog.

2.  Doppelklicken Sie auf **OpenFileDialog**, um dem Formular eine Komponente mit dem Namen **openFileDialog1** hinzuzufügen. Doppelklicken Sie in der **Toolbox** auf **ColorDialog**, um dem Formular eine Komponente mit dem Namen **colorDialog1** hinzuzufügen. (Sie verwenden diese Komponente im nächsten Lernprogrammschritt.) Sie sollten unten im **Windows Forms-Designer** einen Bereich sehen (unterhalb des Formulars **Picture Viewer**), das wie im folgenden Bild ein Symbol für jede der beiden hinzugefügten Dialogfeldkomponenten enthält.

     ![Dialogfeldkomponenten](../ide/media/express_dialogsadded.png)
 **Dialogfeldkomponenten**

3.  Wählen Sie das Symbol **openFileDialog1** im unteren Bereich des **Windows Forms-Designers** aus. Legen Sie zwei Eigenschaften fest:

    -   Legen Sie die Eigenschaft **Filter** auf Folgendes fest (Sie können den Code kopieren und einfügen):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    -   Legen Sie für die Eigenschaft **Title** (Titel) Folgendes fest: **Select a picture file** (Bilddatei auswählen).

         Die Eigenschafteneinstellungen für **Filter** geben die Arten von Dateitypen an, die im Dateidialogfeld **Select a picture** („Bilddatei auswählen“) angezeigt werden.

    > [!NOTE]
    >  Öffnen Sie **Editor** oder **Paint**, und wählen Sie in der Menüleiste **Datei** > **Öffnen** aus, um ein Beispiel für das Dialogfeld **Datei öffnen** in einer anderen Anwendung zu sehen. Im unteren Bereich befindet sich die Dropdownliste **Dateityp**. Sie haben soeben die **Filter**-Eigenschaft in der **OpenFileDialog**-Komponente verwendet, um diese Dropdownliste einzurichten. Beachten Sie auch, dass die Eigenschaften **Title** und **Filter** im **Eigenschaftenfenster** fett sind. Hierdurch kennzeichnet die IDE alle Eigenschaften, deren Standardwerte geändert wurden.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

-   Den nächsten Schritt des Tutorials finden Sie unter [Schritt 8: Schreiben von Code für den Ereignishandler der Schaltfläche „Bild anzeigen“](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

-   Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 6: Benennen der Schaltflächen-Steuerelemente](../ide/step-6-name-your-button-controls.md).

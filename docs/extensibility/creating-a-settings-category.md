---
title: Erstellen einer Einstellungskategorie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f4b2fa9d82181d0eb899bf9680e8a9debd6c50b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739611"
---
# <a name="create-a-settings-category"></a>Erstellen einer Einstellungskategorie

In dieser exemplarischen Vorgehensweise erstellen Sie eine Visual Studio-Einstellungskategorie und verwenden diese zum Speichern von Werten in einer Einstellungsdatei und Wiederherstellen von Werten. Eine Einstellungskategorie ist eine Gruppe verwandter Eigenschaften, die als "benutzerdefinierter Einstellungspunkt" angezeigt werden. d. h. als Kontrollkästchen im Assistenten für **Import- und Exporteinstellungen.** (Sie finden es im Menü **Extras.)** Einstellungen werden als Kategorie gespeichert oder wiederhergestellt, und einzelne Einstellungen werden im Assistenten nicht angezeigt. Weitere Informationen finden Sie unter [Umgebungseinstellungen](../ide/environment-settings.md).

Sie erstellen eine Einstellungskategorie, indem <xref:Microsoft.VisualStudio.Shell.DialogPage> Sie sie aus der Klasse ableiten.

Um diese exemplarische Vorgehensweise zu starten, müssen Sie zuerst den ersten Abschnitt der [Seite Optionen erstellen](../extensibility/creating-an-options-page.md)abschließen. Mit dem resultierenden Optionseigenschaftenraster können Sie die Eigenschaften in der Kategorie untersuchen und ändern. Nachdem Sie die Eigenschaftskategorie in einer Einstellungsdatei gespeichert haben, überprüfen Sie die Datei, um zu sehen, wie die Eigenschaftswerte gespeichert werden.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Erstellen einer Einstellungskategorie
 In diesem Abschnitt verwenden Sie einen benutzerdefinierten Einstellungspunkt, um die Werte der Einstellungskategorie zu speichern und wiederherzustellen.

### <a name="to-create-a-settings-category"></a>So erstellen Sie eine Einstellungskategorie

1. Schließen Sie die [Seite Optionen erstellen ab](../extensibility/creating-an-options-page.md).

2. Öffnen Sie die Datei *VSPackage.resx,* und fügen Sie diese drei Zeichenfolgenressourcen hinzu:

    |name|Wert|
    |----------|-----------|
    |106|Meine Kategorie|
    |107|Meine Einstellungen|
    |108|OptionInteger und OptionFloat|

     Dadurch werden Ressourcen erstellt, die die Kategorie "Meine Kategorie", das Objekt "Meine Einstellungen" und die Kategoriebeschreibung "OptionInteger und OptionFloat" benennen.

    > [!NOTE]
    > Von diesen drei wird nur der Kategoriename nicht im Assistenten für **Import- und Exporteinstellungen** angezeigt.

3. Fügen *MyToolsOptionsPackage.cs*Sie in `float` MyToolsOptionsPackage.cs `OptionFloat` der `OptionPageGrid` Klasse eine Eigenschaft hinzu, die der Klasse benannt ist, wie im folgenden Beispiel gezeigt.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > Die `OptionPageGrid` Kategorie "Meine Kategorie" besteht nun `OptionInteger` aus `OptionFloat`den beiden Eigenschaften und .

4. Fügen <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Sie `MyToolsOptionsPackage` der Klasse eine hinzu und geben Sie ihr den CategoryName "Meine Kategorie", geben Sie ihr den ObjectName "Meine Einstellungen" und setzen Sie isToolsOptionPage auf true. Legen Sie die KategorieResourceID, objectNameResourceID und DescriptionResourceID auf die entsprechenden Zeichenfolgenressourcen-IDs fest, die zuvor erstellt wurden.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Erstellen Sie das Projekt, und starten Sie das Debugging. In der experimentellen Instanz sollten Sie sehen, dass **Meine Rasterseite** jetzt sowohl ganzzahlige als auch schwebende Werte hat.

## <a name="examine-the-settings-file"></a>Überprüfen der Einstellungsdatei
 In diesem Abschnitt exportieren Sie Eigenschaftskategoriewerte in eine Einstellungsdatei. Sie untersuchen die Datei und importieren die Werte dann wieder in die Eigenschaftskategorie.

1. Starten Sie das Projekt im Debugmodus, indem Sie **F5**drücken. Dadurch wird die experimentelle Instanz gestartet.

2. Öffnen Sie das Dialogfeld > **Tools-Optionen.** **Tools**

3. Erweitern Sie in der Strukturansicht im linken Bereich **Meine Kategorie,** und klicken Sie dann auf **Meine Rasterseite**.

4. Ändern Sie den Wert von **OptionFloat** in 3.1416 und **OptionInteger** in 12. Klicken Sie auf **OK**.

5. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**.

     Der Assistent zum **Importieren und Exportieren von Einstellungen** wird angezeigt.

6. Stellen Sie sicher, dass **ausgewählte Umgebungseinstellungen** exportieren ausgewählt ist, und klicken Sie dann auf **Weiter**.

     Die Seite **Einstellungen zum Exportieren auswählen** wird angezeigt.

7. Klicken Sie auf **Meine Einstellungen**.

     Die **Beschreibung** ändert sich in **OptionInteger und OptionFloat**.

8. Stellen Sie sicher, dass **Meine Einstellungen** die einzige Kategorie ist, die ausgewählt ist, und klicken Sie dann auf **Weiter**.

     Die Seite **Name Ihre Einstellungsdatei** wird angezeigt.

9. Benennen Sie die neue Einstellungsdatei *MySettings.vssettings,* und speichern Sie sie in einem entsprechenden Verzeichnis. Klicken Sie auf **Fertig stellen**.

     Auf der Seite **"Vollständig exportieren"** wird berichtet, dass Ihre Einstellungen erfolgreich exportiert wurden.

10. Zeigen Sie im Menü **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**. Suchen Sie *MySettings.vssettings,* und öffnen Sie es.

     Die Eigenschaftenkategorie, die Sie exportiert haben, finden Sie im folgenden Abschnitt der Datei (Ihre GUIDs unterscheiden sich).

    ```
    <Category name="My Category_My Settings"
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"
          RegisteredName="My Category_My Settings">
          PackageName="MyToolsOptionsPackage">
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>
       <PropertyValue name="OptionInteger">12</PropertyValue>
    </Category>
    ```

     Beachten Sie, dass der vollständige Kategoriename durch Hinzufügen eines Unterstrichs zum Kategorienamen gefolgt vom Objektnamen gebildet wird. OptionFloat und OptionInteger werden in der Kategorie zusammen mit ihren exportierten Werten angezeigt.

11. Schließen Sie die Einstellungsdatei, ohne sie zu ändern.

12. Klicken Sie im Menü **Extras** auf **Optionen**, erweitern **Sie Meine Kategorie**, klicken Sie auf Meine **Rasterseite,** und ändern Sie dann den Wert von **OptionFloat** in 1.0 und **OptionInteger** auf 1. Klicken Sie auf **OK**.

13. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, wählen Sie ausgewählte **Umgebungseinstellungen importieren**aus, und klicken Sie dann auf **Weiter**.

     Die Seite **Aktuelle Einstellungen speichern** wird angezeigt.

14. Wählen Sie **Nein, importieren Sie einfach neue Einstellungen** und klicken Sie dann auf **Weiter**.

     Die Seite **"Eine Sammlung von zu importierenden Einstellungen auswählen"** wird angezeigt.

15. Wählen Sie die Datei *MySettings.vssettings* im Knoten **Meine Einstellungen** der Strukturansicht aus. Wenn die Datei nicht in der Strukturansicht angezeigt wird, klicken Sie auf **Durchsuchen,** und suchen Sie sie. Klicken Sie auf **Weiter**.

     Das Dialogfeld **Einstellungen zum Importieren auswählen** wird angezeigt.

16. Stellen Sie sicher, dass **Meine Einstellungen** ausgewählt sind, und klicken Sie dann auf **Fertig stellen**. Wenn die Seite **"Vollständig importieren"** angezeigt wird, klicken Sie auf **Schließen**.

17. Klicken Sie im Menü **Extras** auf **Optionen**, erweitern **Sie Meine Kategorie**, klicken Sie auf Meine **Rasterseite,** und überprüfen Sie, ob die Eigenschaftenkategoriewerte wiederhergestellt wurden.

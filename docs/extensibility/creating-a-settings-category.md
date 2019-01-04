---
title: Erstellen einer Einstellungskategorie | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4653883dbb9d82fd23d5188a2a247db0ec6b69cd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935618"
---
# <a name="create-a-settings-category"></a>Erstellen einer Einstellungskategorie

In dieser exemplarischen Vorgehensweise erstellen Sie eine Kategorie der Visual Studio-Einstellungen und zum Speichern von Werten, und Werte aus einer Datei wiederherstellen. Eine Einstellungskategorie ist eine Gruppe von verwandten Eigenschaften, die als ein "benutzerdefinierter einstellungspunkt"; d. h. als Kontrollkästchen in der **Einstellungen importieren und Exporte** Assistenten. (Sie finden es auf die **Tools** Menü.) Einstellungen werden gespeichert oder als eine Kategorie wiederhergestellt, und der einzelne Einstellungen werden im Assistenten nicht angezeigt. Weitere Informationen finden Sie unter [Umgebungseinstellungen](../ide/environment-settings.md).

Erstellen eine Einstellungskategorie durch Ableiten von der <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse.

Um diese exemplarische Vorgehensweise zu starten, schließen Sie zunächst im ersten Abschnitt des [Erstellen einer Optionsseite](../extensibility/creating-an-options-page.md). Die resultierende Eigenschaftenraster für Serveroptionen können Sie die untersuchen und ändern Sie die Eigenschaften in der Kategorie. Nachdem Sie die Eigenschaftenkategorie in einer Datei speichern, untersuchen Sie die Datei aus, um anzuzeigen, wie Eigenschaftswerte gespeichert werden.

## <a name="prerequisites"></a>Vorraussetzungen
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Erstellen einer Einstellungskategorie
 In diesem Abschnitt verwenden Sie einen benutzerdefinierten einstellungspunkts zu speichern, die Werte der Einstellungskategorie wiederherstellen.

### <a name="to-create-a-settings-category"></a>Zum Erstellen einer Einstellungskategorie

1.  Abschließen der [Erstellen einer Optionsseite](../extensibility/creating-an-options-page.md).

2.  Öffnen der *VSPackage.resx* Datei, und fügen Sie diese drei Zeichenfolgenressourcen hinzu:

    |name|Wert|
    |----------|-----------|
    |106|Meine Kategorie|
    |107|Meine Einstellungen|
    |108|OptionInteger und OptionFloat|

     Dadurch wird die Ressourcen erstellt, diesem Namen der Kategorie "My Category", Objekt "My Settings" und die Beschreibung der Kategorien "OptionInteger und OptionFloat".

    > [!NOTE]
    >  Dieser drei nur die Namen der Kategorie erscheint nicht in der **Einstellungen importieren und exportieren** Assistenten.

3.  In *MyToolsOptionsPackage.cs*, Hinzufügen einer `float` Eigenschaft mit dem Namen `OptionFloat` auf die `OptionPageGrid` Klasse, wie im folgenden Beispiel gezeigt.

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
    >  Die `OptionPageGrid` Kategorie mit dem Namen "My Category" ist jetzt besteht aus den zwei Eigenschaften, `OptionInteger` und `OptionFloat`.

4.  Hinzufügen einer <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> auf die `MyToolsOptionsPackage` -Klasse und weisen Sie ihm die CategoryName "My Category", geben sie den Objektnamen "My Settings" und IsToolsOptionPage auf "true" festgelegt. Legen Sie die CategoryResourceID, ObjectNameResourceID und DescriptionResourceID, auf die entsprechenden Zeichenfolgenressource, die IDs zuvor erstellt haben.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5.  Erstellen Sie das Projekt, und starten Sie das Debugging. In der experimentellen Instanz sollte angezeigt werden, **Meine Rasterseite** verfügt jetzt über Ganzzahl- und Float-Werte.

## <a name="examine-the-settings-file"></a>Überprüfen Sie die Einstellungsdatei
 In diesem Abschnitt exportieren Sie Eigenschaftswerte für die Kategorie, in eine Datei. Sie untersuchen Sie die Datei und importieren Sie dann die Werte wieder in die Eigenschaftskategorie.

1.  Starten Sie das Projekt im Debugmodus durch Drücken von **F5**. Dadurch wird die experimentelle Instanz gestartet.

2.  Öffnen der **Tools** > **Optionen** Dialogfeld.

3.  Erweitern Sie in der Strukturansicht im linken Bereich **My Category** , und klicken Sie dann auf **Meine Rasterseite**.

4.  Ändern Sie den Wert der **OptionFloat** zu 3,1416 und **OptionInteger** bis 12. Klicken Sie auf **OK**.

5.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**.

     Die **Einstellungen importieren und exportieren** -Assistent wird angezeigt.

6.  Stellen Sie sicher, dass **ausgewählte umgebungseinstellungen exportieren** ausgewählt ist, und klicken Sie dann auf **Weiter**.

     Die **Einstellungen für den Export** Seite wird angezeigt.

7.  Klicken Sie auf **Meine Einstellungen**.

     Die **Beschreibung** Änderungen an **OptionInteger und OptionFloat**.

8.  Stellen Sie sicher, dass **Meine Einstellungen** ist die einzige Kategorie, die ausgewählt ist, und klicken Sie dann auf **Weiter**.

     Die **Name der Datei** Seite wird angezeigt.

9. Benennen Sie die neue Einstellungsdatei *MySettings.vssettings* und speichern Sie ihn in ein geeignetes Verzeichnis. Klicken Sie auf **Fertig stellen**.

     Die **vollständige exportieren** Seite gibt an, dass die Einstellungen erfolgreich exportiert wurden.

10. Auf der **Datei** Startmenü **öffnen**, und klicken Sie dann auf **Datei**. Suchen Sie *MySettings.vssettings* und öffnen Sie sie.

     Sie finden die Eigenschaftenkategorie, die Sie im folgenden Abschnitt der Datei exportiert haben (Ihr GUIDs werden abweichen).

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

     Beachten Sie, dass das Hinzufügen von einem Unterstrich, um den Namen der Kategorie, gefolgt vom Objektnamen den Namen der vollständigen Kategorie gebildet wird. OptionFloat und OptionInteger werden in der Kategorie, zusammen mit ihren exportierten Werten.

11. Schließen Sie die Einstellungsdatei, ohne ihn zu ändern.

12. Auf der **Tools** Menü klicken Sie auf **Optionen**, erweitern Sie **My Category**, klicken Sie auf **Meine Rasterseite** und ändern Sie den Wert der  **OptionFloat** 1,0 und **OptionInteger** auf 1. Klicken Sie auf **OK**.

13. Auf der **Tools** Menü klicken Sie auf **Einstellungen importieren und exportieren**Option **ausgewählte umgebungseinstellungen importieren**, und klicken Sie dann auf **Weiter**.

     Die **aktuelle Einstellungen speichern** Seite wird angezeigt.

14. Wählen Sie **Nein, neue Einstellungen importieren** , und klicken Sie dann auf **Weiter**.

     Die **wählen eine Sammlung von Einstellungen für den Import** Seite wird angezeigt.

15. Wählen Sie die *MySettings.vssettings* Datei die **Meine Einstellungen** Knoten der Strukturansicht. Wenn die Datei nicht in der Strukturansicht angezeigt wird, klicken Sie auf **Durchsuchen** finden sie. Klicken Sie auf **Weiter**.

     Die **wählen Sie Einstellungen für den Import** Dialogfeld wird angezeigt.

16. Stellen Sie sicher, dass **Meine Einstellungen** ausgewählt ist, und klicken Sie dann auf **Fertig stellen**. Wenn die **Importvorgang abgeschlossen** klicken Sie mit der Seite angezeigt wird, auf **schließen**.

17. Auf der **Tools** Menü klicken Sie auf **Optionen**, erweitern Sie **My Category**, klicken Sie auf **Meine Rasterseite** und stellen Sie sicher, dass die Eigenschaftswerte für die Kategorie haben wurde wiederhergestellt.
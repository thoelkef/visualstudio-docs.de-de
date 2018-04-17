---
title: Erstellen einer Einstellungskategorie | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22a625466dd8a94ba1dbe67ef6f05bec68954d2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-settings-category"></a>Erstellen einer Einstellungskategorie
In dieser exemplarischen Vorgehensweise erstellen Sie eine Kategorie der Visual Studio-Einstellungen und verwendet, um Werte zu speichern und Werte aus einer Datei wiederherstellen. Eine Einstellungskategorie ist eine Gruppe verwandter Eigenschaften, die als "Benutzerdefinierte Einstellungen Verwaltungspunkt;" angezeigt werden. d. h. als ein Kontrollkästchen in der **Einstellungen importieren und Exporten** Assistenten. (Sie finden es auf die **Tools** Menü.) Einstellungen gespeichert werden, oder als Kategorie wiederhergestellt und individuelle Einstellungen im Assistenten nicht angezeigt werden. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
 Erstellen eine Einstellungskategorie durch Ableitung von der <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse.  
  
 Um dieser exemplarischen Vorgehensweise beginnen, müssen Sie zuerst Ausführen der erste Abschnitt der [Erstellen einer Optionsseite](../extensibility/creating-an-options-page.md). Resultierende Optionen Eigenschaftenraster können Sie überprüfen und Ändern der Eigenschaften in der Kategorie. Nachdem Sie die Eigenschaftenkategorie in eine Datei speichern, untersuchen Sie die Datei, um zu sehen, wie die Eigenschaftswerte gespeichert sind.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-settings-category"></a>Erstellen einer Einstellungskategorie  
 In diesem Abschnitt verwenden Sie eine benutzerdefinierte einstellungspunkte speichern und Wiederherstellen der Werte der Einstellungskategorie an.  
  
#### <a name="to-create-a-settings-category"></a>Zum Erstellen einer Einstellungskategorie  
  
1.  Führen Sie die [Erstellen einer Optionsseite](../extensibility/creating-an-options-page.md).  
  
2.  Öffnen Sie die Datei VSPackage.resx, und fügen Sie diese drei Zeichenfolgenressourcen hinzu:  
  
    |name|Wert|  
    |----------|-----------|  
    |106|Meine Kategorie|  
    |107|Meine Einstellungen|  
    |108|OptionInteger und OptionFloat|  
  
     Dadurch wird die Ressourcen erstellt, diesem Namen der Kategorie "Meine Category", das Objekt "Meine Einstellungen" und die Beschreibung der Kategorie "OptionInteger und OptionFloat".  
  
    > [!NOTE]
    >  Dieser drei wird nur die Namen der Kategorie in den Assistenten zum Importieren und Exportieren von Einstellungen nicht angezeigt.  
  
3.  In MyToolsOptionsPackage.cs, Hinzufügen einer `float` Eigenschaft mit dem Namen `OptionFloat` auf die `OptionPageGrid` Klasse, wie im folgenden Beispiel gezeigt.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
        private float optionFloat = 3.14F;  
  
        [Category("My Options")]  
        [DisplayName("My Integer option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
        [Category("My Options")]  
        [DisplayName("My Float option")]  
        [Description("My float option")]  
        public float OptionFloat  
        {  
            get { return optionFloat; }  
            set { optionFloat = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  Die `OptionPageGrid` Kategorie mit dem Namen "Meine Category" jetzt die beiden Eigenschaften besteht aus `OptionInteger` und `OptionFloat`.  
  
4.  Hinzufügen einer <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> auf die `MyToolsOptionsPackage` -Klasse und weisen Sie ihm die CategoryName "Meine Category", geben Sie ihm den Objektnamen "Meine Einstellungen" und IsToolsOptionPage auf "true" festgelegt. Legen Sie die CategoryResourceID, ObjectNameResourceID und DescriptionResourceID auf der entsprechenden Zeichenfolgenressource zuvor erstellten IDs an.  
  
    ```csharp  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. In der experimentellen Instanz sollte angezeigt werden, **Meine Rasterseite** verfügt jetzt über Ganzzahl-und Fließkommawerte.  
  
## <a name="examining-the-settings-file"></a>Untersuchen die Einstellungsdatei  
 In diesem Abschnitt exportieren Sie Eigenschaftswerte für die Kategorie in eine Datei. Sie untersuchen Sie die Datei und importieren Sie dann die Werte wieder in die Eigenschaftskategorie.  
  
1.  Starten Sie das Projekt im Debugmodus befinden, durch Drücken von F5. Dadurch wird die experimentelle Instanz gestartet.  
  
2.  Öffnen der **Extras / Optionen** Dialogfeld.  
  
3.  Erweitern Sie in der Strukturansicht im linken Bereich **Meine Kategorie** , und klicken Sie dann auf **Meine Rasterseite**.  
  
4.  Ändern Sie den Wert der **OptionFloat** auf 3,1416 und **OptionInteger** bis 12. Klicken Sie auf **OK**.  
  
5.  Auf der **Tools** Menü klicken Sie auf **Einstellungen importieren und exportieren**.  
  
     Die **Einstellungen importieren und exportieren** -Assistent wird angezeigt.  
  
6.  Stellen Sie sicher, dass **ausgewählte umgebungseinstellungen exportieren** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
     Die **wählen Sie Einstellungen für den Export** Seite wird angezeigt.  
  
7.  Klicken Sie auf **Meine Einstellungen**.  
  
     Die **Beschreibung** ändert sich in **OptionInteger und OptionFloat**.  
  
8.  Stellen Sie sicher, dass **Meine Einstellungen** ist die einzige Kategorie, die ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
     Die **Namen der Einstellungsdatei** Seite wird angezeigt.  
  
9. Benennen Sie die neue Einstellungsdatei `MySettings.vssettings` und speichern Sie ihn in ein entsprechendes Verzeichnis. Klicken Sie auf **Fertig stellen**.  
  
     Die **vollständige exportieren** Seite gibt an, dass Ihre Einstellungen wurden erfolgreich exportiert wurden.  
  
10. Auf der **Datei** Sie im Menü **öffnen**, und klicken Sie dann auf **Datei**. Suchen Sie `MySettings.vssettings` und öffnen Sie sie.  
  
     Sie können die Eigenschaftenkategorie finden, die Sie im folgenden Abschnitt der Datei exportiert haben (die GUIDs werden unterschiedlich sind).  
  
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
  
     Beachten Sie, dass der vollständige Kategorienamen durch das Hinzufügen von Unterstrich auf den Namen der Kategorie, gefolgt vom Namen Hierarchienamens generiert wird. OptionFloat und OptionInteger werden in der Kategorie zusammen mit ihren exportierten Werten.  
  
11. Schließen Sie die Einstellungsdatei, ohne ihn ändern.  
  
12. Auf der **Tools** Menü klicken Sie auf **Optionen**, erweitern Sie **Meine Kategorie**, klicken Sie auf **Meine Rasterseite** und ändern Sie den Wert des  **OptionFloat** 1.0 und **OptionInteger** auf 1. Klicken Sie auf **OK**.  
  
13. Auf der **Tools** Menü klicken Sie auf **Einstellungen importieren und exportieren**Option **ausgewählte umgebungseinstellungen importieren**, und klicken Sie dann auf **Weiter**.  
  
     Die **aktuelle Einstellungen speichern** Seite wird angezeigt.  
  
14. Wählen Sie **Nein, neue Einstellungen importieren** , und klicken Sie dann auf **Weiter**.  
  
     Die **wählen Sie eine Sammlung von Einstellungen für den Import** Seite wird angezeigt.  
  
15. Wählen Sie die `MySettings.vssettings` in der Datei die **Meine Einstellungen** Knoten der Strukturansicht. Wenn die Datei nicht in der Strukturansicht angezeigt wird, klicken Sie auf **Durchsuchen** und gefunden. Klicken Sie auf **Weiter**.  
  
     Die **wählen Sie Einstellungen für den Import** Dialogfeld wird angezeigt.  
  
16. Stellen Sie sicher, dass **Meine Einstellungen** ausgewählt ist, und klicken Sie dann auf **Fertig stellen**. Wenn die **Importvorgang abgeschlossen** Seite angezeigt wird, klicken Sie auf **schließen**.  
  
17. Auf der **Tools** Menü klicken Sie auf **Optionen**, erweitern Sie **Meine Kategorie**, klicken Sie auf **Meine Rasterseite** und stellen Sie sicher, dass die Kategorie Eigenschaftswerte haben wurde wiederhergestellt.
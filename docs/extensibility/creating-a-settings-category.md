---
title: "Erstellen einer Einstellungskategorie | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Erstellen von Kategorien profileinstellungen"
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
caps.latest.revision: 39
caps.handback.revision: 39
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen einer Einstellungskategorie
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise müssen Sie eine Visual Studio\-Einstellungen erstellen und verwenden, um Werte zu speichern und Werte aus einer Datei wiederherstellen. Einstellungskategorie ist eine Gruppe verwandter Eigenschaften, die als "Benutzerdefinierte Einstellungen Punkt;" angezeigt werden. d. h. als Kontrollkästchen in der **Einstellungen importieren und Exporte** Assistenten. \(Sie finden es auf die **Tools** Menü.\) Einstellungen gespeichert werden, oder als eine Kategorie wiederhergestellt, und einzelne Einstellungen werden nicht im Assistenten angezeigt. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Erstellen Sie eine Settings\-Kategorie durch Ableitung von der <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse.  
  
 Um diese exemplarische Vorgehensweise beginnen, müssen Sie zunächst den ersten Abschnitt des [Erstellen eine Optionsseite](../extensibility/creating-an-options-page.md). Die resultierende Eigenschaftenraster für Serveroptionen können Sie die überprüfen und Ändern der Eigenschaften in der Kategorie. Nachdem Sie die Kategorie in einer Datei speichern, untersuchen Sie die Datei aus, um anzuzeigen, wie Eigenschaftswerte gespeichert werden.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen einer Einstellungskategorie  
 In diesem Abschnitt verwenden Sie einen benutzerdefinierten Einstellungen zu speichern, die Werte der Einstellungskategorie wiederherstellen.  
  
#### Erstellen eine Einstellungskategorie  
  
1.  Führen Sie die [Erstellen eine Optionsseite](../extensibility/creating-an-options-page.md).  
  
2.  Öffnen Sie die Datei VSPackage.resx, und fügen Sie diese drei Zeichenfolgenressourcen hinzu:  
  
    |Name|Wert|  
    |----------|----------|  
    |106|Meine Kategorie|  
    |107|Meine Einstellungen|  
    |108|OptionInteger und OptionFloat|  
  
     Dadurch wird die Ressourcen, Name der Kategorie "My Category", das Objekt "Meine Einstellungen" und die Beschreibung der Kategorie "OptionInteger und OptionFloat" erstellt.  
  
    > [!NOTE]
    >  Diese drei wird nur die Namen der Kategorie in den Assistenten zum Importieren und Exportieren von Einstellungen nicht angezeigt.  
  
3.  Fügen Sie in MyToolsOptionsPackage.cs, eine `float` Eigenschaft mit dem Namen `OptionFloat` auf die `OptionPageGrid` Klasse, wie im folgenden Beispiel gezeigt.  
  
    ```c#  
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
    >  Die `OptionPageGrid` Kategorie mit dem Namen "My Category" jetzt besteht aus zwei Eigenschaften `OptionInteger` und `OptionFloat`.  
  
4.  Hinzufügen einer <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> die `MyToolsOptionsPackage` \-Klasse und weisen sie CategoryName "My Category", geben sie den Objektnamen "Meine Einstellungen" und IsToolsOptionPage auf True festgelegt. Legen Sie die CategoryResourceID, ObjectNameResourceID und DescriptionResourceID auf der entsprechenden Zeichenfolgenressource zuvor erstellten IDs.  
  
    ```c#  
    [ProvideProfileAttribute(typeof(OptionPageGrid),   
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]  
    ```  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. In der experimentellen Instanz sollten angezeigt werden, **Meine Rasterseite** verfügt jetzt über Ganzzahl\-und Fließkommawerte.  
  
## Untersuchen die Einstellungsdatei  
 In diesem Abschnitt exportieren Sie Eigenschaftswerte für die Kategorie in eine Datei. Untersuchen Sie die Datei, und importieren Sie dann die Werte wieder in der Kategorie.  
  
1.  Starten Sie das Projekt im Debugmodus, durch Drücken von F5. Dadurch wird die experimentelle Instanz gestartet.  
  
2.  Öffnen Sie die **Extras \/ Optionen** Dialogfeld.  
  
3.  Erweitern Sie in der Strukturansicht im linken Bereich **Meine Kategorie** und klicken Sie dann auf **Meine Rasterseite**.  
  
4.  Ändern Sie den Wert der **OptionFloat** zu 3.1416 und **OptionInteger** 12. Klicken Sie auf **OK**.  
  
5.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**.  
  
     Die **Einstellungen importieren und exportieren** \-Assistent wird angezeigt.  
  
6.  Stellen Sie sicher, dass **ausgewählte umgebungseinstellungen exportieren** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
     Die **Wählen Sie Einstellungen für den Export** Seite wird angezeigt.  
  
7.  Klicken Sie auf **Meine Einstellungen**.  
  
     Die **Beschreibung** ändert sich in **OptionInteger und OptionFloat**.  
  
8.  Stellen Sie sicher, dass **Meine Einstellungen** ist die einzige Kategorie, die ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
     Die **Name der Einstellungsdatei** Seite wird angezeigt.  
  
9. Nennen Sie die neue Einstellungsdatei `MySettings.vssettings` und in ein geeignetes Verzeichnis zu speichern. Klicken Sie auf **Fertig stellen**.  
  
     Die **vollständige exportieren** Seite meldet, dass die Einstellungen erfolgreich exportiert wurden.  
  
10. Auf der **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**. Suchen Sie `MySettings.vssettings` und öffnen Sie es.  
  
     Sie finden die Kategorie, die Sie im folgenden Abschnitt der Datei exportiert \(die GUIDs werden unterscheiden\).  
  
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
  
     Beachten Sie, dass die vollständige Kategorienamen zusätzlich einen Unterstrich, den Namen der Kategorie, gefolgt vom Objektnamen gebildet wird. OptionFloat und OptionInteger werden in der Kategorie zusammen mit ihren Werten exportierten.  
  
11. Schließen Sie die Datei ohne Änderung.  
  
12. Auf der **Tools** Menü klicken Sie auf **Optionen**, erweitern Sie **Meine Kategorie**, klicken Sie auf **Meine Rasterseite** und ändern Sie den Wert der **OptionFloat** 1.0 und **OptionInteger** auf 1. Klicken Sie auf **OK**.  
  
13. Auf der **Tools** Menü klicken Sie auf **Einstellungen importieren und exportieren**, auf **ausgewählte umgebungseinstellungen importieren**, und klicken Sie dann auf **Weiter**.  
  
     Die **aktuelle Einstellungen speichern** Seite wird angezeigt.  
  
14. Wählen Sie **Nein, neue Einstellungen importieren** und klicken Sie dann auf **Weiter**.  
  
     Die **Wählen Sie eine Auflistung der Einstellungen für den Import** Seite wird angezeigt.  
  
15. Wählen Sie die `MySettings.vssettings` Datei der **Meine Einstellungen** Knoten in der Strukturansicht angezeigt. Wenn die Datei nicht in der Strukturansicht angezeigt wird, klicken Sie auf **Durchsuchen** und finden. Klicken Sie auf **Weiter**.  
  
     Die **Wählen Sie Einstellungen für den Import** das Dialogfeld wird angezeigt.  
  
16. Stellen Sie sicher, dass **Meine Einstellungen** ausgewählt ist, und klicken Sie dann auf **Fertig stellen**. Wenn die **Importieren abgeschlossen** Seite angezeigt wird, klicken Sie auf **Schließen**.  
  
17. Auf der **Tools** Menü klicken Sie auf **Optionen**, erweitern Sie **Meine Kategorie**, klicken Sie auf **Meine Rasterseite** und stellen Sie sicher, dass die Kategorie Eigenschaftswerte wiederhergestellt wurden.
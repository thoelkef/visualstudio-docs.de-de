---
title: "Exemplarische Vorgehensweise: Automatisches Laden von Toolboxelementen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolbox [Visual Studio SDK], Hinzufügen von Steuerelementen mithilfe von Reflexion"
  - "Reflexion, Toolbox"
ms.assetid: b03c0d62-3be0-475f-b1d9-725dee993ad6
caps.latest.revision: 56
caps.handback.revision: 56
manager: "douge"
---
# Exemplarische Vorgehensweise: Automatisches Laden von Toolboxelementen
Diese exemplarische Vorgehensweise veranschaulicht, wie ein verwaltetes VSPackage Reflexion verwenden kann, um alle <xref:System.Drawing.Design.ToolboxItem>\-Elemente, die von seiner eigenen Assembly bereitgestellt werden, automatisch zu laden.  
  
> [!NOTE]
>  Die empfohlene Methode zum Hinzufügen benutzerdefinierter Steuerelemente zur Toolbox ist die Verwendung der Vorlagen für Toolbox\-Steuerelemente, die im Lieferumfang von Visual Studio SDK enthalten sind und automatisches Laden unterstützen. Dieses Thema wird aus Gründen der Abwärtskompatibilität beibehalten und behandelt das Hinzufügen von vorhandenen Steuerelementen zur Toolbox und fortgeschrittene Toolbox\-Entwicklung.  
>   
>  Weitere Informationen zum Erstellen von Toolbox\-Steuerelementen mithilfe der Vorlagen finden Sie unter [Gewusst wie: Erstellen eines Toolbox\-Steuerelements, das Windows Forms verwendet](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) und [Erstellen ein WPF\-Toolbox\-Steuerelement](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Diese exemplarische Vorgehensweise enthält folgende Schritte:  
  
1.  Fügen Sie alle **Toolbox**\-Steuerelemente in den VSPackage\-Objekten mithilfe von <xref:System.ComponentModel.ToolboxItemAttribute>, <xref:System.Drawing.ToolboxBitmapAttribute> und <xref:System.ComponentModel.DisplayNameAttribute> hinzu, und registrieren Sie sie ordnungsgemäß.  
  
2.  Erstellen Sie die beiden folgenden Steuerelemente, und fügen Sie der **Toolbox** für jedes ein Symbol hinzu:  
  
    -   Fügen Sie ein Steuerelement hinzu, und verwenden Sie dazu die standardmäßige Klasse <xref:System.Drawing.Design.ToolboxItem>.  
  
    -   Fügen Sie ein weiteres Steuerelement unter Verwendung einer benutzerdefinierten Klasse hinzu, die aus der <xref:System.Drawing.Design.ToolboxItem>\-Klasse abgeleitet ist.  
  
3.  Registrieren Sie das VSPackage als Anbieter von <xref:System.Drawing.Design.ToolboxItem>\-Objekten, die der <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>\-Klasse angehören.  
  
4.  Verwenden Sie Reflexion, um eine Liste aller <xref:System.Drawing.Design.ToolboxItem>\-Objekte zu generieren, die das VSPackage beim Laden bereitstellt.  
  
5.  Erstellen Sie einen Ereignishandler für die Ereignisse <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> und <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>. Damit wird sichergestellt, dass die <xref:System.Drawing.Design.ToolboxItem>\-Objekte des VSPackage ordnungsgemäß geladen werden.  
  
6.  Implementieren Sie einen Befehl für das VSPackage, um die erneute Initialisierung der **Toolbox** zu erzwingen.  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Übersicht über die Erweiterung von Visual Studio](../Topic/Extending%20Visual%20Studio%20Overview.md).  
  
## Speicherorte für die VSPackage\-Projektvorlage  
 Die VSPackage\-Projektvorlage finden Sie an drei verschiedenen Stellen im Dialogfeld **Neues Projekt**:  
  
1.  Unter Visual Basic\-Erweiterbarkeit. Die Standardsprache des Projekts ist Visual Basic.  
  
2.  Unter C\#\-Erweiterbarkeit. Die Standardsprache des Projekts ist C\#.  
  
3.  Unter der Erweiterbarkeit für andere Projekttypen. Die Standardsprache des Projekts ist C\+\+.  
  
## Erstellen eines verwalteten VSPackage  
  
#### So erstellen Sie das LoadToolboxMembers\-VSPackage  
  
1.  Erstellen Sie ein VSPackage mit dem Namen `LoadToolboxMembers`. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Menübefehls mithilfe der Visual Studio\-Paketvorlage](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  Fügen Sie einen Menübefehl hinzu.  
  
     Geben Sie dem Befehl für Visual Basic den Namen `Initialize LoadToolboxMembers VB` oder für Visual C\# den Namen `Initialize LoadToolboxMembers CS`.  
  
 Wenn Sie diese exemplarische Vorgehensweise für mehrere Sprachen ausführen, müssen Sie das Projekt aktualisieren, um die generierten Assemblys eindeutig zu machen.  
  
#### So machen Sie Visual Basic\- und Visual C\#\-VSPackages eindeutig  
  
1.  Für [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]:  
  
    -   Öffnen Sie im **Lösungsmappen\-Explorer** die Projekteigenschaften, und wählen Sie die Registerkarte **Anwendung** aus.  
  
         Ändern Sie den Assemblynamen in `LoadToolboxMembersVB`, und ändern Sie den Standardnamespace in `Company.LoadToolboxMembersVB`.  
  
2.  Für [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]:  
  
    1.  Öffnen Sie im **Lösungsmappen\-Explorer** die Projekteigenschaften, und wählen Sie die Registerkarte **Anwendung** aus.  
  
         Ändern Sie den Assemblynamen in `LoadToolboxMembersCS`, und ändern Sie den Standardnamespace in `Company.LoadToolboxMembersCS`.  
  
    2.  Öffnen Sie im Code\-Editor die LoadToolboxMembersPackage\-Klasse.  
  
         Um die Refactoringtools zum Umbenennen des vorhandenes Namespaces verwenden zu können, klicken Sie mit der rechten Maustaste auf den vorhandenen Namespacenamen, `LoadToolboxMembers`, zeigen Sie auf **Umgestalten**, und klicken Sie dann auf **Umbenennen**. Ändern Sie den Namen in `LoadToolboxMembersCS`.  
  
3.  Speichern Sie alle Änderungen.  
  
#### So fügen Sie unterstützende Verweise hinzu  
  
1.  Fügen Sie im LoadToolboxMembers\-Projekt einen Verweis auf die .NET Framework\-Komponente <xref:System.Drawing.Design?displayProperty=fullName> hinzu, wie hier dargestellt.  
  
    1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das LoadToolboxMembers\-Projekt, und klicken Sie dann auf **Hinzufügen**, **Verweis**.  
  
    2.  Doppelklicken Sie auf der Registerkarte **.NET** im Dialogfeld **Verweise** auf **System.Drawing.Design**.  
  
2.  Fügen Sie für Visual Basic die folgenden Namespaces zur importierten Namespaceliste im Projekt hinzu:  
  
    -   Company.LoadToolboxMembersVB  
  
    -   System  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
#### So testen Sie den generierten Code  
  
1.  Kompilieren und starten Sie das VSPackage in der experimentellen Visual Studio\-Struktur.  
  
2.  Klicken Sie im Menü **Extras** auf **LoadToolboxMembers VB initialisieren** oder auf **LoadToolboxMembers CS initialisieren**.  
  
     Dadurch wird ein Meldungsfeld geöffnet, das Text enthält, der angibt, dass der Handler für Menüelemente des Pakets aufgerufen wurde.  
  
3.  Schließen Sie die experimentelle Version von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
## Erstellen eines Toolbox\-Steuerelements  
 In diesem Abschnitt erstellen und registrieren Sie ein Benutzersteuerelement, `Control1`, das ein zugeordnetes standardmäßiges **Toolbox**element deklariert. Weitere Informationen zum Erstellen von Windows Forms\-Steuerelementen und der <xref:System.Drawing.Design.ToolboxItem>\-Klasse finden Sie unter [Entwickeln von Windows Forms\-Steuerelementen zur Entwurfszeit](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
#### So erstellen Sie ein Toolbox\-Steuerelement, das mit einem standardmäßigen ToolboxItem verwendet wird  
  
1.  Fügen Sie im **Projektmappen\-Explorer** ein <xref:System.Windows.Forms.UserControl>\-Objekt zum LoadToolboxMembers\-Projekt hinzu, wie hier gezeigt:  
  
    1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt **LoadToolboxMembers**, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Benutzersteuerelement**.  
  
    2.  Ändern Sie im Dialogfeld **Neues Element hinzufügen** den Namen für [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] in `Control1.vb` oder für [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] in `Control1.cs`.  
  
         Weitere Informationen zum Hinzufügen neuer Elemente zu einem Projekt finden Sie unter [NIB: Vorgehensweise: Hinzufügen neuer Projektelemente](http://msdn.microsoft.com/de-de/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).  
  
     Das neue Steuerelement wird in der Designansicht geöffnet.  
  
2.  Ziehen Sie aus der **Toolbox** ein **Schaltflächen**\-Steuerelement \(das sich in der Kategorie **Allgemeine Steuerelemente** befindet\) auf den Designer.  
  
3.  Doppelklicken Sie auf die Schaltfläche, die Sie gerade erstellt haben. Dadurch wird ein Ereignishandler für das <xref:System.Windows.Forms.Control.Click>\-Ereignis der Schaltfläche erstellt. Aktualisieren Sie den Ereignishandler mithilfe des folgenden Codes:  
  
     [!code-cs[LoadToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_1.cs)]
     [!code-vb[LoadToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_1.vb)]  
  
4.  Ändern Sie den Konstruktor des Steuerelements, um den Schaltflächentext nach dem Aufrufen der `InitializeComponent`\-Methode festzulegen:  
  
     [!code-cs[LoadToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_2.cs)]
     [!code-vb[LoadToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_2.vb)]  
  
5.  Fügen Sie der Datei Attribute hinzu, um dem VSPackage das Abfragen der übergebenen <xref:System.Drawing.Design.ToolboxItem>\-Klasse zu ermöglichen:  
  
     [!code-cs[LoadToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_3.cs)]
     [!code-vb[LoadToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_3.vb)]  
  
6.  Speichern Sie die Datei.  
  
 Beim folgenden Vorgang erstellen und registrieren Sie außerdem ein zweites Benutzersteuerelement, `Control2`, und ein zugeordnetes benutzerdefiniertes **Toolbox**element, `Control2_ToolboxItem`, das von der <xref:System.Drawing.Design.ToolboxItem>\-Klasse abgeleitet wird.  
  
#### So erstellen Sie ein Toolbox\-Steuerelement für die Verwendung einer von ToolboxItem abgeleiteten benutzerdefinierten Klasse  
  
1.  Erstellen Sie ein zweites Benutzersteuerelement mit dem Namen `Control2`. Doppelklicken Sie auf das Formular, um die Codedatei zu öffnen.  
  
2.  Fügen Sie den in der Klasse verwendeten Namespaces `System.Drawing.Design` und `System.Globalization` hinzu.  
  
     [!code-cs[LoadToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_4.cs)]
     [!code-vb[LoadToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_4.vb)]  
  
3.  Fügen Sie eine Schaltfläche und einen Click\-Ereignishandler für die Schaltfläche hinzu, und aktualisieren Sie den Konstruktor des Steuerelements in der gleichen Weise wie beim ersten Steuerelement.  
  
4.  Fügen Sie der Datei die Attribute <xref:System.ComponentModel.DisplayNameAttribute>, <xref:System.ComponentModel.DescriptionAttribute>, <xref:System.ComponentModel.ToolboxItemAttribute> und <xref:System.Drawing.ToolboxBitmapAttribute> hinzu.  
  
     Diese Attribute ermöglichen dem VSPackage das Abfragen nach einer <xref:System.Drawing.Design.ToolboxItem>\-Klasse.  
  
     Weitere Informationen und Beispiele zum Erstellen von benutzerdefinierten <xref:System.Drawing.Design.ToolboxItem>\-Objekten finden Sie in der Diskussion auf der <xref:System.Drawing.Design.ToolboxItem>\-Referenzseite.  
  
     Zusammen mit den vorhergehenden Änderungen sollte Ihre zweite Steuerelementklasse so ähnlich aussehen wie der folgende Code. Das Symbol `Control2_ToolboxMenu` bleibt bis nach der Ausführung des nächsten Schritts undefiniert.  
  
     [!code-cs[LoadToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_5.cs)]
     [!code-vb[LoadToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_5.vb)]  
  
5.  Erstellen Sie eine Klasse mit dem Namen `Control2_ToolboxItem`. Dieses <xref:System.Drawing.Design.ToolboxItem> wird für das zweite Steuerelement erstellt und der **Toolbox** hinzugefügt. Auf die Klasse muss `SerializableAttribute` angewendet werden.  
  
     [!code-cs[LoadToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_6.cs)]
     [!code-vb[LoadToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_6.vb)]  
  
6.  Speichern Sie die Datei.  
  
## Einbetten von Bitmap\-Symbolen  
 Die beiden früher verwendeten Instanzen von <xref:System.Drawing.ToolboxBitmapAttribute> weisen darauf hin, dass das Projekt die beiden Steuerelemente mithilfe der folgenden Symbole darstellt:  
  
-   `Control1.bmp`, das sich in dem Namespace befindet, der das erste Steuerelement enthält.  
  
-   `Control2.bmp`, das sich in dem Namespace befindet, der das zweite Steuerelement enthält.  
  
#### So betten Sie Bitmap\-Symbole für das ToolboxItem ein  
  
1.  Fügen Sie dem Projekt zwei neue Bitmaps hinzu, wie hier dargestellt.  
  
    1.  Klicken Sie mit der rechten Maustaste auf das `LoadToolboxMembers`\-Projekt.  
  
    2.  Zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.  
  
    3.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Bitmapdatei** aus, und geben Sie der Datei den Namen `Control1.bmp`.  
  
    4.  Wiederholen Sie diese Schritte für die zweite Bitmap, und benennen Sie sie `Control2.bmp`.  
  
         Bei diesem Vorgang wird jede Bitmap im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Bitmap\-Editor geöffnet.  
  
2.  Legen Sie die Größe jedes Symbols auf 16 x 16 fest, wie hier gezeigt.  
  
    1.  Klicken Sie für jede Bitmap im Menü **Ansicht** auf **Eigenschaftenfenster**.  
  
    2.  Legen Sie im Fenster **Eigenschaften** die **Höhe** und **Breite** auf 16 fest.  
  
3.  Verwenden Sie den Bitmap\-Editor in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], um für jedes Symbol ein Bild zu erstellen.  
  
4.  Klicken Sie im **Projektmappen\-Explorer** auf jede der Bitmapdateien, und legen Sie dann im Fenster **Eigenschaften** die Eigenschaft **Buildvorgang** auf **Eingebettete Ressource** fest.  
  
5.  Speichern Sie alle geöffneten Dateien.  
  
## Ändern der VSPackage\-Implementierung  
 Die standardmäßige Implementierung des VSPackage muss geändert werden, um die folgenden Punkte zu erreichen:  
  
-   Registrieren der Unterstützung als Elementanbieter für die **Toolbox**.  
  
-   Abrufen einer Liste von <xref:System.Drawing.Design.ToolboxItem>\-Objekten, die vom VSPackage unterstützt werden.  
  
-   Laden des <xref:System.Drawing.Design.ToolboxItem>\-Objekts in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Toolbox**, wenn die Ereignisse <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> und <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> verarbeitet werden.  
  
 Die nächste Vorgehensweise zeigt, wie die Paketimplementierung geändert wird.  
  
#### So ändern Sie die Paketimplementierung in einen Toolbox\-Elementanbieter für das VSPackage  
  
1.  Öffnen Sie die \-Datei „LoadToolboxMembersPackage.cs“ oder „LoadToolboxMembersPackage.vb“ im Code\-Editor.  
  
2.  Ändern Sie die Deklaration der `LoadToolboxMembersPackage`\-Klasse, die die Implementierung der <xref:Microsoft.VisualStudio.Shell.Package>\-Klasse in der Projektmappe darstellt, in folgender Weise:  
  
    1.  Fügen Sie der `LoadToolboxMembersPackage`\-Klassendatei die folgenden Namespace\-Direktiven hinzu.  
  
         [!code-cs[LoadToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_7.cs)]
         [!code-vb[LoadToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_7.vb)]  
  
    2.  Registrieren Sie das VSPackage als <xref:System.Drawing.Design.ToolboxItem>\-Klasse, indem Sie eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> hinzufügen.  
  
        > [!NOTE]
        >  Das einzige Argument von <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> ist die Version von <xref:System.Drawing.Design.ToolboxItem>, die vom VSPackage bereitgestellt wird. Durch Änderung dieses Werts erzwingen Sie, dass die IDE das VSPackage lädt, auch wenn eine zwischengespeicherte frühere Version der <xref:System.Drawing.Design.ToolboxItem>\-Klasse vorhanden ist.  
  
    3.  Fügen Sie der `LoadToolboxMembersPackage`\-Klasse die beiden folgenden neuen `private`\-Felder hinzu:  
  
         Einen <xref:System.Collections.ArrayList>\-Member mit dem Namen `ToolboxItemList` zur Aufnahme einer Liste der <xref:System.Drawing.Design.ToolboxItem>\-Objekte, die die `LoadToolboxMembersPackage`\-Klasse verwaltet.  
  
         Eine <xref:System.String> mit dem Namen `CategoryTab`, die die **Toolbox**\-Kategorie oder \-Registerkarte enthält, die zur Aufnahme der <xref:System.Drawing.Design.ToolboxItem>\-Objekte dient, die von der `LoadToolboxMembersPackage`\-Klasse verwaltet werden.  
  
     Das Ergebnis dieser Änderung ähnelt dem folgenden Code:  
  
     [!code-cs[LoadToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_8.cs)]
     [!code-vb[LoadToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_8.vb)]  
  
3.  Erweitern Sie den Bereich „Paketmember“, um die `Initialize`\-Methode zu ändern und folgende Schritte auszuführen:  
  
    -   Abonnieren Sie für [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] die Ereignisse <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> und <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>.  
  
    -   Rufen Sie die `CreateItemList`\-Methode auf, um das <xref:System.Collections.ArrayList>\-Objekt `ToolboxItemList` zu füllen. Die `ToolboxItemList` enthält eine Liste aller Toolboxelemente, die von `LoadToolboxMembersPackage` verwaltet werden.  
  
     [!code-cs[LoadToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_9.cs)]
     [!code-vb[LoadToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_9.vb)]  
  
4.  Hinzufügen von zwei Methoden, `CreateItemList` und `CreateToolboxItem`, um mithilfe von Metadaten Instanzen der <xref:System.Drawing.Design.ToolboxItem>\-Objekte zu konstruieren, die in der `LoadToolboxMembers`\-Assembly verfügbar sind, wie hier dargestellt:  
  
     [!code-cs[LoadToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_10.cs)]
     [!code-vb[LoadToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_10.vb)]  
  
5.  Implementieren der `OnRefreshToolbox`\-Methode zur Verarbeitung des <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized>\-Ereignisses und des <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>\-Ereignisses.  
  
     Die `OnRefreshToolbox`\-Methode verwendet die Liste der <xref:System.Drawing.Design.ToolboxItem>\-Objekte, die im `ToolboxItemList`\-Member der `LoadToolboxMembersPackage`\-Klasse enthalten ist. Sie führt außerdem die folgenden Aktionen aus:  
  
    -   Entfernt alle <xref:System.Drawing.Design.ToolboxItem>\-Objekte, die bereits in der durch die Variable `CategoryTab` definierten Toolboxkategorie vorhanden sind.  
  
    -   Fügt neue Instanzen aller <xref:System.Drawing.Design.ToolboxItem>\-Objekte, die in `ToolboxItemList` aufgelistet sind, zur Kategorieregisterkarte für das VSProject hinzu.  
  
    -   Legt die aktive **Toolbox**\-Registerkarte auf die Kategorieregisterkarte für das VSProject fest.  
  
     [!code-cs[LoadToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_11.cs)]
     [!code-vb[LoadToolboxMembers#11](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_11.vb)]  
  
    > [!NOTE]
    >  Als Übung könnten Sie einen Mechanismus zum Testen der Version des VSPackage oder der Elemente entwickeln, bei dem nur dann eine Aktualisierung durchgeführt wird, wenn sich die Version des VSPackages oder die Version der <xref:System.Drawing.Design.ToolboxItem> geändert hat.  
  
## Initialisieren der Toolbox  
  
#### So implementieren Sie einen Befehl zum Initialisieren der Toolbox  
  
-   Ändern Sie die Handlermethode des Menüelementbefehls `MenuItemCallBack`, wie hier gezeigt.  
  
    1.  Ersetzen Sie die vorhandene Implementierung von `MenuItemCallBack` durch den folgenden Code:  
  
         [!code-cs[LoadToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_12.cs)]
         [!code-vb[LoadToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_12.vb)]  
  
## Erstellen und Ausführen der Projektmappe  
 Sie können das Produkt dieser exemplarischen Vorgehensweise mit einer Instanz von Visual Studio ausführen, die in der experimentellen Struktur ausgeführt wird.  
  
#### So führen Sie diese exemplarische Vorgehensweise aus  
  
1.  Klicken Sie in Visual Studio im Menü **Erstellen** auf **Projektmappe neu erstellen**.  
  
2.  Drücken Sie F5, um eine zweite Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in der experimentellen Registrierungsstruktur zu starten.  
  
     Weitere Informationen zum Verwenden der experimentellen Struktur finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
3.  Klicken Sie auf das Menü **Tools**.  
  
     Oben im Menü sollte ein Befehl mit den Namen **LoadToolboxMembers VB initialisieren** oder **LoadToolboxMembers CS initialisieren** zusammen mit einem Symbol mit der Zahl 1 angezeigt werden.  
  
4.  Erstellen Sie eine neue [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\- oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Windows Forms\-Anwendung.  
  
     Ein <xref:System.Windows.Forms.Form>\-basierter Designer sollte angezeigt werden.  
  
5.  Ziehen Sie eins oder beide der neuen Steuerelemente in der Kategorie **Exemplarische Vorgehensweise: LoadToolboxMembers VB** oder **Exemplarische Vorgehensweise: LoadToolboxMembers CS** der **Toolbox** im Designer auf das Formular.  
  
    > [!NOTE]
    >  Wenn die **Toolbox** nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Toolbox**. Wenn die Kategorieregisterkarte für das VSPackage nicht in der **Toolbox** angezeigt wird, initialisieren Sie die **Toolbox** erneut, indem Sie im Menü **Tools** auf **LoadToolboxMembers VB initialisieren** oder **LoadToolboxMembers CS initialisieren** klicken.  
  
6.  Erstellen Sie die Windows\-Anwendung, indem Sie im Menü **Erstellen** auf **Projektmappe neu erstellen** klicken.  
  
7.  Führen Sie die Anwendung aus, indem Sie im Menü **Debuggen** entweder auf **Starten ohne Debugging** oder auf **Debugging starten** klicken.  
  
8.  Wenn die Anwendungen ausgeführt werden, klicken Sie auf eins der Steuerelemente, die Sie der Anwendung hinzugefügt haben.  
  
     Ein Nachrichtenfeld wird angezeigt, das entweder `"Hello world from Company.LoadToolboxMembers.Control1"` oder  `"Hello world from Company.LoadToolboxMembers.Control2"` anzeigt.  
  
## Analyse der Implementierung  
  
### Erstellen von Toolbox\-Steuerelementen  
 Die Attribute, die `Control1` und `Control2` zugewiesenen sind, werden von der Methode `CreateItemList` zum Abfragen der `Assembly` nach verfügbaren **Toolbox**\-Steuerelementen verwendet.  
  
-   Das <xref:System.ComponentModel.ToolboxItemAttribute> führt die beiden folgenden Funktionen aus:  
  
    -   Zuweisung von <xref:System.ComponentModel.ToolboxItemAttribute> zu `Control1` und `Control2`, was angibt, dass es sich bei beiden um Toolbox\-Steuerelemente handelt.  
  
    -   Argument für den Konstruktor <xref:System.ComponentModel.ToolboxItemAttribute>, das angibt, ob zum Hinzufügen des Steuerelements zur **Toolbox** die standardmäßige Klasse <xref:System.Drawing.Design.ToolboxItem> oder eine von <xref:System.Drawing.Design.ToolboxItem> abgeleitete benutzerdefinierte Klasse verwendet wird.  
  
         Die `Control1` zugewiesene Instanz von <xref:System.ComponentModel.ToolboxItemAttribute> wird mit dem Argument `true` erstellt, was angibt, dass eine standardmäßige <xref:System.Drawing.Design.ToolboxItem>\-Klasse verwendet wird, wenn das Steuerelement der **Toolbox** hinzugefügt wird.  
  
         Die Instanz von <xref:System.ComponentModel.ToolboxItemAttribute>, die `Control2` zugewiesen wird, wird mit dem <xref:System.Type> einer Klasse erstellt, die aus <xref:System.Drawing.Design.ToolboxItem> abgeleitet ist, `Control2_ToolboxItem`.  
  
-   Die <xref:System.Drawing.ToolboxBitmapAttribute>\-Klasse gibt Bitmaps an, die von der Umgebung zur Identifizierung der Steuerelemente verwendet werden.  
  
     Durch das Einbetten einer Bitmap in eine Assembly durch Festlegen ihrer Eigenschaft **Buildvorgang** auf **Eingebettete Ressource** wird die Bitmap in den Namespace der Assembly eingefügt. Daher kann auf `Control1.bmp` als `Company.LoadToolboxMembers.Control1.bmp` verwiesen werden.  
  
     <xref:System.Drawing.ToolboxBitmapAttribute> unterstützt einen Konstruktor, der diesen vollständigen Pfad als Argument akzeptiert. Beispielsweise kann eine <xref:System.Drawing.ToolboxBitmapAttribute>\-Klasse mithilfe von `[ToolboxBitmap("Company.LoadToolboxMembers.Control1.bmp")]` auf `Control1` angewendet werden.  
  
     Um Raum für Flexibilität zu geben, wird in dieser exemplarischen Vorgehensweise ein Konstruktor verwendet, der eine <xref:System.Type>\-Klasse als erstes Argument des <xref:System.Drawing.ToolboxBitmapAttribute>\-Konstruktors akzeptiert. Der zum Identifizieren der Bitmapdatei verwendete Namespace wird bei <xref:System.Type> abgerufen und vor dem Basisnamen der Bitmap eingefügt.  
  
     Da das <xref:System.Type>\-Objekt, das <xref:Microsoft.VisualStudio.Shell.Package> implementiert, `LoadToolboxMembers`, sich im Namespace `Company.LoadToolboxMembers` befindet, ist `[ToolboxBitmap(typeof(Control1), "Control1.bmp")]` gleichbedeutend mit `[ToolboxBitmap("Company.LoadToolboxMembers.Control1.bmp")]`.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> gibt den Namen des Steuerelements in der **Toolbox** an.  
  
### Registrieren eines Toolbox\-Steuerelementanbieters  
 Das Anwenden der <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>\-Klasse auf die Klasse, die <xref:Microsoft.VisualStudio.Shell.Package> implementiert, wirkt sich auf die Registrierungseinstellungen des resultierenden VSPackage aus. Weitere Informationen über die Registrierungseinstellungen für einen <xref:System.Drawing.Design.ToolboxItem>\-Anbieter finden Sie unter [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md).  
  
 Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Umgebung verwendet das Versionsargument des <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>\-Konstruktors, um die Zwischenspeicherung von VSPackages zu verwalten, die Elemente für die **Toolbox** zur Verfügung stellen. Nachdem ein VSPackage geladen wurde, um **Toolbox**\-Elemente zur Verfügung zu stellen, wird eine zwischengespeicherte Version des VSPackage verwendet, bis eine Änderung an der registrierten Version des Anbieters auftritt. Wenn Sie daher das Produkt dieser exemplarischen Vorgehensweise nach dem Erstellen ändern möchten, achten Sie darauf, das Versionsargument des <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute>\-Konstruktors zu ändern, der auf `AddToolboxItem` angewendet wird. Beispielsweise sollte `[ProvideToolboxItems(1)]` in `[ProvideToolboxItems(2)]` geändert werden. Wenn die Version nicht geändert wird, lädt die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Umgebung keine der vorgenommenen Änderungen.  
  
 In dieser exemplarischen Vorgehensweise ist das VSPackage so konfiguriert, dass nur **Toolbox**\-Steuerelemente zu Verfügung gestellt werden, die das Standardformat der Zwischenablage unterstützen. Eine Liste der standardmäßigen Zwischenablageformate finden Sie unter [Erweitern der Toolbox](../misc/extending-the-toolbox.md). Wenn Sie weitere Zwischenablageformate unterstützen möchten oder sich entscheiden, überhaupt kein Standardformat zu unterstützen, wenden Sie das Attribut <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> auf die `LoadToolboxMembersPackage`\-Klasse an. Weitere Informationen zum Registrieren eines **Toolbox**\-Steuerelementanbieters finden Sie unter [Erweiterte Toolbox\-Steuerelemententwicklung](../misc/advanced-toolbox-control-development.md).  
  
### Hinzufügen von Steuerelementen zur Toolbox  
 Die Funktionalität von `CreateItemList` emuliert die in <xref:System.Drawing.Design.ToolboxService.System%23Drawing%23Design%23IToolboxService%23GetToolboxItems%2A> verfügbaren Elemente.  
  
 Die `CreateItemList`\-Methode untersucht nur die nicht abstrakten <xref:System.Type>\-Objekte, die die <xref:System.ComponentModel.IComponent>\-Schnittstellen implementieren.  
  
## Nächste Schritte  
 Die Verwendung von <xref:System.Drawing.Design.ToolboxService.System%23Drawing%23Design%23IToolboxService%23GetToolboxItems%2A> anstelle von `CreateItemList` würde das aus dieser exemplarischen Vorgehensweise resultierende Produkt stabiler machen.  
  
 Sie könnten darüber hinaus auch `CreateItemList` so verändern, dass <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> zum Laden von Steuerelementen in die **Toolbox** auf der Basis einer Textliste verwendet wird, die in die `LoadToolboxMembers`\-Assembly eingebettet ist.  
  
## Siehe auch  
 [Erweitern der Toolbox](../misc/extending-the-toolbox.md)   
 [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md)   
 [Erweiterte Toolbox\-Steuerelemententwicklung](../misc/advanced-toolbox-control-development.md)   
 [Werkzeugkasten, exemplarische Vorgehensweisen](../misc/toolbox-walkthroughs.md)
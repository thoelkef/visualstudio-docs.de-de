---
title: "Exemplarische Vorgehensweise: Dynamisches Anpassen der Konfiguration von Toolboxelementen | Microsoft Docs"
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
  - "Toolbox [Visual Studio SDK], Hinzufügen von Steuerelementen (benutzerdefinierte Formate)"
ms.assetid: 761f44b7-c748-4ff5-921f-fc4f71784b0e
caps.latest.revision: 45
caps.handback.revision: 45
manager: "douge"
---
# Exemplarische Vorgehensweise: Dynamisches Anpassen der Konfiguration von Toolboxelementen
Diese exemplarische Vorgehensweise zeigt, wie ein verwaltetes VSPackage für die <xref:System.Drawing.Design.ToolboxItem>\-Objekte dynamische Konfigurationsunterstützung bieten kann.  
  
> [!NOTE]
>  Am einfachsten lassen sich benutzerdefinierte Steuerelemente zur Toolbox mithilfe der Vorlagen für Toolbox\-Steuerelemente hinzufügen, die im Visual Studio SDK enthalten sind. Dieses Thema bezieht sich auf die erweiterte Toolboxentwicklung.  
>   
>  Weitere Informationen dazu, wie Sie Toolbox\-Steuerelemente mithilfe der Vorlagen erstellen können, finden Sie unter [Gewusst wie: Erstellen eines Toolbox\-Steuerelements, das Windows Forms verwendet](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) und [Erstellen ein WPF\-Toolbox\-Steuerelement](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Diese exemplarische Vorgehensweise enthält folgende Schritte:  
  
1.  Fügen Sie alle **Toolbox**\-Steuerelemente im VSPackage\-Objekt mithilfe der Klassen <xref:System.ComponentModel.ToolboxItemAttribute> und <xref:System.Drawing.ToolboxBitmapAttribute> hinzu, und registrieren Sie sie ordnungsgemäß.  
  
2.  Erstellen Sie die beiden folgenden Steuerelemente, und fügen Sie der **Toolbox** für jedes ein Symbol hinzu:  
  
    -   ein Steuerelement, das ein zugeordnetes standardmäßiges <xref:System.Drawing.Design.ToolboxItem> deklariert, und  
  
    -   ein Steuerelement, das ein zugeordnetes benutzerdefiniertes **Toolbox**element deklariert, das von der <xref:System.Drawing.Design.ToolboxItem>\-Klasse abgeleitet ist.  
  
3.  Schreiben Sie eine Implementierung von <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>, und führen Sie die Registrierung durch Ausführen der folgenden Schritte aus:  
  
    1.  Definieren Sie eine Filterklasse, die von der <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>\-Klasse abgeleitet ist und die <xref:System.Drawing.Design.ToolboxItem>\-Instanzen angibt, die von dieser Implementierung verwendet werden.  
  
    2.  Wenden Sie ein <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>, das auf die Filterklasse verweist, auf die Klasse an, die die <xref:Microsoft.VisualStudio.Shell.Package>\-Klasse für das VSPackage implementiert.  
  
4.  Registrieren Sie das VSPackage als Anbieter von <xref:System.Drawing.Design.ToolboxItem>\-Objekten. Wenden Sie dazu das <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> auf die Klasse an, die die <xref:Microsoft.VisualStudio.Shell.Package>\-Klasse für das VSPackage implementiert.  
  
5.  Verwenden Sie zum Zeitpunkt des Ladens des Pakets die Reflektion, um eine Liste aller <xref:System.Drawing.Design.ToolboxItem>\-Objekte zu generieren, die das VSPackage bereitstellt.  
  
6.  Erstellen Sie einen Ereignishandler für die Ereignisse <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> und <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>. So ist sichergestellt, dass die <xref:System.Drawing.Design.ToolboxItem>\-Objekte des VSPackage korrekt geladen werden.  
  
7.  Implementieren Sie einen Befehl für das VSPackage, um die erneute Initialisierung der **Toolbox** zu erzwingen.  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Speicherorte für die Projektvorlage für das Visual Studio\-Paket  
 Die Projektvorlage für das Visual Studio\-Paket finden Sie an drei verschiedenen Stellen im Dialogfeld **Neues Projekt**:  
  
1.  Unter Visual Basic\-Erweiterbarkeit. Die Standardsprache des Projekts ist Visual Basic.  
  
2.  Unter C\#\-Erweiterbarkeit. Die Standardsprache des Projekts ist C\#.  
  
3.  Unter der Erweiterbarkeit für andere Projekttypen. Die Standardsprache des Projekts ist C\+\+.  
  
## Erstellen eines verwalteten VSPackage  
 Führen Sie die folgenden Schritte aus, um ein verwaltetes VSPackage zu erstellen.  
  
#### So erstellen Sie ein verwaltetes VSPackage zum Bereitstellen von Toolboxelementen  
  
1.  Erstellen Sie ein VSPackage mit dem Namen `ItemConfiguration`. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Menübefehls mithilfe der Visual Studio\-Paketvorlage](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  Fügen Sie in der Vorlage **Visual Studio\-Paket** einen Menübefehl hinzu.  
  
     Geben Sie dem Befehl für Visual Basic den Namen `Initialize ItemConfigurationVB` oder für Visual C\# den Namen `Initialize ItemConfigurationCS`.  
  
3.  Fügen Sie für [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] der Liste der importierten Namespaces im generierten Projekt die folgenden Namespaces hinzu:  
  
    -   Company.ItemConfiguration  
  
    -   System  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
4.  Fügen Sie einen Verweis auf die .NET Framework\-Komponente <xref:System.Drawing.Design?displayProperty=fullName> hinzu.  
  
 Wenn Sie diese exemplarische Vorgehensweise für mehrere Sprachen ausführen, müssen Sie das Projekt aktualisieren, um die generierten Assemblys eindeutig zu machen.  
  
#### So machen Sie Visual Basic\- und Visual C\#\-VSPackages eindeutig  
  
1.  Für [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]:  
  
    1.  Öffnen Sie die Projekteigenschaften, und wählen Sie die Registerkarte **Anwendung** aus.  
  
         Ändern Sie den Assemblynamen in `ItemConfigurationVB`, und ändern Sie den Standardnamespace in `Company.ItemConfigurationVB`.  
  
    2.  Wählen Sie die Registerkarte **Verweise** aus.  
  
         Aktualisieren Sie die Liste der importierten Namespaces.  
  
         Entfernen Sie "Company.ItemConfiguration".  
  
         Fügen Sie "Company.ItemConfigurationVB" hinzu.  
  
2.  Für [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]:  
  
    1.  Öffnen Sie die Projekteigenschaften, und wählen Sie die Registerkarte **Anwendung** aus.  
  
         Ändern Sie den Assemblynamen in `ItemConfigurationCS`, und ändern Sie den Standardnamespace in `Company.ItemConfigurationCS`.  
  
    2.  Öffnen Sie im Code\-Editor die ItemConfigurationPackage\-Klasse.  
  
         Um die Refactoringtools zum Umbenennen des vorhandenes Namespaces verwenden zu können, klicken Sie mit der rechten Maustaste auf den vorhandenen Namespacenamen, `ItemConfiguration`, zeigen Sie auf **Umgestalten**, und klicken Sie dann auf **Umbenennen**. Ändern Sie den Namen in `ItemConfigurationCS`.  
  
3.  Speichern Sie alle Änderungen.  
  
#### So testen Sie den generierten Code  
  
1.  Kompilieren und starten Sie das VSPackage in der experimentellen Visual Studio\-Struktur.  
  
2.  Klicken Sie im Menü **Tools** auf **Elementkonfiguration VB initialisieren** oder **Elementkonfiguration CS initialisieren**.  
  
     Daraufhin öffnet sich ein Meldungsfeld, dessen Text angibt, dass der Handler für das Menüelement des Pakets aufgerufen wurde.  
  
3.  Schließen Sie die experimentelle Version von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
## Erstellen von Toolbox\-Steuerelementen  
 In diesem Abschnitt erstellen und registrieren Sie ein Benutzersteuerelement, `Control1`, das ein zugeordnetes standardmäßiges **Toolbox**element deklariert. Sie erstellen und registrieren außerdem ein zweites Benutzersteuerelement, `Control2`, und ein zugeordnetes benutzerdefiniertes **Toolbox**element, `Control2_ToolboxItem`, das von der <xref:System.Drawing.Design.ToolboxItem>\-Klasse abgeleitet wird. Weitere Informationen zum Erstellen von Windows Forms\-Steuerelementen und <xref:System.Drawing.Design.ToolboxItem>\-Klassen finden Sie unter [Entwickeln von Windows Forms\-Steuerelementen zur Entwurfszeit](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md).  
  
#### So erstellen Sie standardmäßige und benutzerdefinierte Toolboxelemente  
  
1.  Verwenden Sie die Anweisungen unter [Exemplarische Vorgehensweise: Automatisches Laden von Toolboxelementen](../misc/walkthrough-autoloading-toolbox-items.md) zum Erstellen eines standardmäßigen **Toolbox**elements und eines benutzerdefinierten **Toolbox**elements wie folgt.  
  
    1.  Beenden Sie den Vorgang "So erstellen Sie ein **Toolbox**\-Steuerelement, das mit einem standardmäßigen ToolboxItem verwendet wird". Aktualisieren Sie das <xref:System.ComponentModel.DescriptionAttribute>, sodass es auf dieses Projekt verweist.  
  
         Der resultierende Code für die `Control1`\-Klasse sollte dem folgenden Code ähneln:  
  
         [!code-cs[DynamicToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_1.cs)]
         [!code-vb[DynamicToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_1.vb)]  
  
    2.  Beenden Sie den Vorgang unter "So erstellen Sie ein **Toolbox**\-Steuerelement für die Verwendung einer von ToolboxItem abgeleiteten benutzerdefinierten Klasse". Aktualisieren Sie das <xref:System.ComponentModel.DescriptionAttribute>, sodass es auf dieses Projekt verweist.  
  
         Der resultierende Code für die Klassen `Control2` und `Control2_ToolboxItem` sollte dem folgenden Code ähneln:  
  
         [!code-vb[DynamicToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_2.vb)]
         [!code-cs[DynamicToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_2.cs)]  
  
2.  Speichern Sie die Dateien.  
  
## Einbetten von Bitmap\-Symbolen  
 Das <xref:System.Drawing.ToolboxBitmapAttribute>\-Attribut, das auf jedes Steuerelement angewendet wird, gibt an, welches Symbol dem Steuerelement zugeordnet wird. Erstellen Sie die Bitmaps für beide Steuerelemente, und nennen Sie sie wie folgt:  
  
-   `Control1.bmp` für die `Control1`\-Klasse.  
  
-   `Control2.bmp` für die `Control2`\-Klasse.  
  
#### So betten Sie ein Bitmap\-Symbol für ein Toolboxelement ein  
  
1.  Fügen Sie dem Projekt folgendermaßen eine neue Bitmapdatei hinzu:  
  
    1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das VSPackage\-Projekt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.  
  
    2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Bitmapdatei** aus, und geben Sie den Namen der Bitmapdatei ein.  
  
2.  Verwenden Sie den Bitmap\-Editor, um wie folgt ein 16 x 16\-Symbol zu erstellen.  
  
    1.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.  
  
    2.  Legen Sie im Fenster **Eigenschaften** die **Höhe** und **Breite** auf 16 fest.  
  
    3.  Verwenden Sie Editor, um das Symbolbild zu erstellen.  
  
3.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Bitmapelement, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Legen Sie die Eigenschaft **Buildaktion** auf **Eingebettete Ressource** fest.  
  
5.  Speichern Sie alle geöffneten Dateien.  
  
## Hinzufügen eines dynamischen Toolbox\-Konfigurationsanbieters  
 In diesem Abschnitt erstellen und registrieren Sie eine Klasse, die die <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>\-Schnittstelle implementiert. Diese Klasse wird von der integrierten Entwicklungsumgebung \(IDE\) von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instanziiert und verwendet, um **Toolbox**\-Steuerelemente zu konfigurieren.  
  
> [!NOTE]
>  Da die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Umgebung eine Instanz der Implementierung von <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> instanziiert, implementieren Sie nicht die <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>\-Schnittstelle für die Klasse, die <xref:Microsoft.VisualStudio.Shell.Package> für ein VSPackage implementiert.  
  
#### So erstellen und registrieren Sie ein Konfigurationsobjekt für ein Toolbox\-Steuerelement  
  
1.  Fügen Sie im **Projektmappen\-Explorer**dem ItemConfiguration\-Projekt eine Klasse hinzu, und nennen Sie sie `ToolboxConfig`.  
  
2.  Fügen Sie der Datei die folgenden Namespaceanweisungen hinzu.  
  
     [!code-cs[DynamicToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_3.cs)]
     [!code-vb[DynamicToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_3.vb)]  
  
3.  Stellen Sie sicher, dass die `ToolboxConfig`\-Klasse `public` ist und die <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>\-Schnittstelle implementiert.  
  
4.  Wenden Sie ein <xref:System.Runtime.InteropServices.GuidAttribute> und ein <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> auf die `ToolboxConfig`\-Klasse an`.`  
  
    -   Für [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] verwenden Sie den Namen einer Assembly von `"ItemConfigurationVB, Version=*, Culture=*, PublicKeyToken=*"`.  
  
    -   Für [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] verwenden Sie den Namen einer Assembly von `"ItemConfigurationCS, Version=*, Culture=*, PublicKeyToken=*"`.  
  
     So wird die `ToolboxConfig`\-Klasse darauf beschränkt, <xref:System.Drawing.Design.ToolboxItem>\-Objekte zu bearbeiten, die von der Assembly bereitgestellt werden, die das aktuelle VSPackage enthält.  
  
     [!code-cs[DynamicToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_4.cs)]
     [!code-vb[DynamicToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_4.vb)]  
  
     Sie können eine GUID generieren, indem Sie auf **GUID erstellen** im Menü **Tools** klicken. Wählen Sie das **Format mit eckigen Klammern** aus, klicken Sie auf **Kopieren**, und fügen Sie die GUID dann in Ihren Code ein. Ändern Sie das Schlüsselwort `GUID` in `Guid`.  
  
5.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A>\-Methode der <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>\-Schnittstelle, damit die Methode nur auf die beiden <xref:System.Drawing.Design.ToolboxItem>\-Klassen `Control1` und `Control2` angewendet wird.  
  
     Die Implementierung von <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> wendet Instanzen von <xref:System.ComponentModel.ToolboxItemFilterAttribute> auf die beiden <xref:System.Drawing.Design.ToolboxItem>\-Objekte an. Dies bewirkt Folgendes:  
  
    -   Das <xref:System.Drawing.Design.ToolboxItem>, das von `Control1` implementiert wird, steht nur in der **Toolbox** für Designer zur Verfügung, die <xref:System.Windows.Forms.UserControl>\-Objekte verarbeiten.  
  
    -   Das <xref:System.Drawing.Design.ToolboxItem>, das von `Control2` implementiert wird, steht nicht in der **Toolbox** für Designer zur Verfügung, die <xref:System.Windows.Forms.UserControl>\-Objekte verarbeiten.  
  
     [!code-cs[DynamicToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_5.cs)]
     [!code-vb[DynamicToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_5.vb)]  
  
## Ändern der VSPackage\-Implementierung  
 Die standardmäßige Implementierung des VSPackage, die von der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Paketvorlage bereitgestellt wird, muss geändert werden, damit die folgenden Aktionen ausgeführt werden können:  
  
-   Registrieren als **Toolbox**\-Elementanbieter.  
  
-   Registrieren der Klasse, die die dynamische **Toolbox**\-Steuerelementkonfiguration für das VSPackage bereitstellt.  
  
-   Verwenden des <xref:System.Drawing.Design.ToolboxService> um alle <xref:System.Drawing.Design.ToolboxItem>\-Objekte zu laden, die von der VSPackage\-Assembly bereitgestellt werden.  
  
-   Verarbeiten von <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized>\- und <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>\-Ereignissen.  
  
#### So ändern Sie die Paketimplementierung für einen Toolbox\-Elementanbieter im VSPackage  
  
1.  Öffnen Sie im Code\-Editor die ItemConfigurationPackage\-Klasse.  
  
2.  Ändern Sie die Deklaration der `ItemConfigurationPackage`\-Klasse, die die Implementierung der <xref:Microsoft.VisualStudio.Shell.Package>\-Klasse in der Projektmappe ist.  
  
    1.  Fügen Sie der Datei die folgenden Namespaceanweisungen hinzu.  
  
         [!code-vb[DynamicToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_6.vb)]
         [!code-cs[DynamicToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_6.cs)]  
  
    2.  Um das VSPackage als Anbieter von **Toolbox**elementen zu registrieren, wenden Sie ein <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> auf das Paket an. Um die `ToolboxConfig`\-Klasse als Anbieter einer dynamischen Konfiguration eines **Toolbox**\-Steuerelements zu registrieren, wenden Sie ein <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> auf das Paket an.  
  
         [!code-vb[DynamicToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_7.vb)]
         [!code-cs[DynamicToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_7.cs)]  
  
        > [!NOTE]
        >  Das einzige Argument von <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> ist die Version von <xref:System.Drawing.Design.ToolboxItem>, die von dem VSPackage bereitgestellt wird. Durch Änderung dieses Werts erzwingen Sie, dass die IDE das VSPackage lädt, auch wenn eine zwischengespeicherte frühere Version von <xref:System.Drawing.Design.ToolboxItem> vorhanden ist.  
  
    3.  Erstellen Sie wie folgt zwei neue `private`\-Felder in der `ItemConfiguration`Klasse:  
  
         Einen <xref:System.Collections.ArrayList>\-Member mit dem Namen `ToolboxItemList` zur Aufnahme einer Liste der <xref:System.Drawing.Design.ToolboxItem>\-Objekte, die die `ItemConfiguration`\-Klasse verwaltet.  
  
         Eine <xref:System.String> mit dem Namen `CategoryTab`, die die **Toolbox**\-Registerkarte enthält, die zur Aufnahme der <xref:System.Drawing.Design.ToolboxItem>\-Objekte dient, die die `ItemConfiguration`\-Klasse verwaltet.  
  
         [!code-vb[DynamicToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_8.vb)]
         [!code-cs[DynamicToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_8.cs)]  
  
     Das Ergebnis dieser Änderung ähnelt dem folgenden Code:  
  
     [!code-vb[DynamicToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_9.vb)]
     [!code-cs[DynamicToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_9.cs)]  
  
3.  Definieren Sie eine `OnRefreshToolbox`\-Methode zur Verarbeitung des <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized>\-Ereignisses und des <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>Ereignisses.  
  
     Die `OnRefreshToolbox`\-Methode verwendet die Liste der <xref:System.Drawing.Design.ToolboxItem>\-Objekte, die im `ToolboxItemList`\-Feld enthalten ist, und führt die folgenden Schritte aus:  
  
    -   Sie entfernt alle <xref:System.Drawing.Design.ToolboxItem>\-Objekte aus der **Toolbox**\-Registerkarte, die durch das `CategoryTab`\-Feld definiert ist.  
  
    -   Sie fügt der **Toolbox**\-Registerkarte neue Instanzen aller <xref:System.Drawing.Design.ToolboxItem>\-Objekte hinzu, die im `ToolboxItemList`\-Feld aufgelistet sind.  
  
    -   Sie legt die  **Toolbox**\-Registerkarte als aktive Registerkarte fest.  
  
     [!code-vb[DynamicToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_10.vb)]
     [!code-cs[DynamicToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_10.cs)]  
  
4.  Registrieren Sie für [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] im Konstruktor die `OnRefreshToolbox`\-Methode als Ereignishandler für das <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized>\-Ereignis und das <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>\-Ereignis.  
  
     [!code-cs[DynamicToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_11.cs)]  
  
5.  Ändern Sie die `Initialize`\-Methode in `ItemConfigurationPackage` zum Ausfüllen des `ToolboxItemList`\-Felds, indem Sie die <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A>\-Methode der <xref:System.Drawing.Design.ToolboxService?displayProperty=fullName>Klasse aufrufen. Der **Toolbox**dienst ruft alle **Toolbox**\-Elementklassen ab, die in der aktuell ausgeführten Assembly definiert sind. Das `ToolboxItemList`\-Feld wird von den **Toolbox**\-Ereignishandlern verwendet, um die **Toolbox**elemente zu laden.  
  
     Fügen Sie den folgenden Code am Ende der `Initialize`\-Methode hinzu.  
  
     [!code-vb[DynamicToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_12.vb)]
     [!code-cs[DynamicToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_12.cs)]  
  
    > [!NOTE]
    >  Als Übung könnten Sie einen Mechanismus zum Testen der Version des VSPackage oder der Elemente entwickeln, bei dem nur dann eine Aktualisierung durchgeführt wird, wenn sich die VSPackage\-Version oder die Version der <xref:System.Drawing.Design.ToolboxItem> geändert hat.  
  
## Initialisieren der Toolbox  
  
#### So implementieren Sie einen Befehl zum Initialisieren der Toolbox  
  
-   Ändern Sie in der `ItemConfigurationPackage`\-Klasse die `MenuItemCallBack`\-Methode, die der Befehlshandler des Menüelements ist.  
  
     Ersetzen Sie die vorhandene Implementierung der `MenuItemCallBack`\-Methode mit dem folgenden Code:  
  
     [!code-vb[DynamicToolboxMembers#13](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_13.vb)]
     [!code-cs[DynamicToolboxMembers#13](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_13.cs)]  
  
## Erstellen und Ausführen der Projektmappe  
 Sie können das Produkt dieser exemplarischen Vorgehensweise mit einer Instanz von Visual Studio ausführen, die in der experimentellen Struktur ausgeführt wird.  
  
#### So führen Sie diese exemplarische Vorgehensweise aus  
  
1.  Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe neu erstellen**.  
  
2.  Drücken Sie F5, um eine zweite Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in der experimentellen Registrierungsstruktur zu starten.  
  
     Weitere Informationen zum Verwenden der experimentellen Struktur finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
3.  Klicken Sie auf das Menü **Tools**.  
  
     Ein Befehl mit dem Namen **Initialisieren ItemConfiguration VB** oder **Initialisieren ItemConfiguration CS** wird oben im Menü zusammen mit einem Symbol mit der Zahl 1 angezeigt.  
  
4.  Erstellen Sie eine neue [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\- oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Windows Forms\-Anwendung.  
  
     Der <xref:System.Windows.Forms.Form>\-basierte Designer wird geöffnet.  
  
5.  Fügen Sie dem Projekt ein Benutzersteuerelement hinzu.  
  
     Ein Benutzersteuerelement\-Designer wird angezeigt.  
  
6.  Öffnen Sie die **Toolbox**, heften Sie sie an, und wechseln Sie zwischen den beiden Designansichten.  
  
     Welches **Toolbox**element sichtbar und welches ausgeblendet ist, hängt davon ab, welcher Designer den Fokus hat.  
  
7.  Ziehen Sie das erste **Toolbox**element auf das Benutzersteuerelement, um dem Benutzersteuerelement eine Instanz von `Control1` hinzuzufügen.  
  
8.  Ziehen Sie das zweite **Toolbox**element auf das Formular, um dem Formular eine Instanz von `Control2` hinzuzufügen.  
  
9. Erstellen Sie die Windows\-Anwendung.  
  
     Das Benutzersteuerelement für die Anwendung ist jetzt in der **Toolbox** verfügbar.  
  
10. Fügen Sie das Benutzersteuerelement der Anwendung dem Formular hinzu, erstellen Sie dann die Anwendung neu, und führen Sie sie aus.  
  
     Wenn die Anwendung ausgeführt wird, klicken Sie auf jedes Steuerelement im Formular, um das zugeordnete Meldungsfeld anzuzeigen.  
  
## Analyse der Implementierung  
 In der Assembly, die in dieser exemplarischen Vorgehensweise erstellt wurde, werden nur <xref:System.Drawing.Design.ToolboxItem>\-Objekte von der <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A>\-Methode der `ToolboxConfg`\-Klasse behandelt, da der `assemblyFilter`\-Parameter im <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute>\-Klassenkonstruktor vorhanden ist.  
  
 Das bedeutet, dass immer dann, wenn die **ItemConfiguration Walkthrough**\-Kategorie in der **Toolbox** aktiv ist, die <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A>\-Methode der `ToolboxConfg`\-Klasse aufgerufen wird und <xref:System.ComponentModel.ToolboxItemFilterAttribute>\-Instanzen auf die <xref:System.Drawing.Design.ToolboxItem>\-Objekte angewendet werden, die von `Control1` und `Control2` implementiert werden.  
  
## Siehe auch  
 [Erweitern der Toolbox](../misc/extending-the-toolbox.md)   
 [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md)   
 [Erweiterte Toolbox\-Steuerelemententwicklung](../misc/advanced-toolbox-control-development.md)   
 [Werkzeugkasten, exemplarische Vorgehensweisen](../misc/toolbox-walkthroughs.md)
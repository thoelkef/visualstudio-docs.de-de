---
title: 'Exemplarische Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44bafccdb3c99032678a808ba3f82f9f14558b3e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893428"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Exemplarische Vorgehensweise: Erstellen einer SharePoint-projekterweiterung
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie eine Erweiterung für SharePoint-Projekte erstellt werden. Sie können eine projekterweiterung verwenden, zum Reagieren auf Ereignisse auf Projektebene, z. B. wenn ein Projekt hinzugefügt, gelöscht oder umbenannt wird. Sie können auch benutzerdefinierte Eigenschaften hinzufügen oder reagieren, wenn ein Eigenschaftswert ändert. Im Gegensatz zu projektelementerweiterungen darf nicht projekterweiterungen einen bestimmten Typ von SharePoint-Projekt zugeordnet sein. Bei der Erstellung einer projekterweiterung lädt die Erweiterung wird in der jede Art von SharePoint-Projekt geöffnet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 In dieser exemplarischen Vorgehensweise erstellen Sie eine benutzerdefinierte boolesche Eigenschaft, die erstellt werden, einem SharePoint-Projekt hinzugefügt wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Bei Festlegung auf **"true"**, fügt die neue Eigenschaft oder zugeordnet wird, handelt es sich bei einem Bildordner für die Ressource zu Ihrem Projekt. Bei Festlegung auf **"false"**, Bilderordner wird entfernt, sofern vorhanden. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung für SharePoint-Projekte, der Folgendes ausführt:  
  
    -   Das Fenster "Eigenschaften" wird eine benutzerdefinierte Eigenschaft hinzugefügt. Die Eigenschaft gilt für alle SharePoint-Projekt.  
  
    -   Verwendet das Objektmodell der SharePoint-Projekt ein Projekt einen zugeordneten Ordner hinzu.  
  
    -   Verwendet die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Automatisierungsobjektmodell (DTE) aus dem Projekt einen zugeordneten Ordner zu löschen.  
  
-   Erstellen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterungspakets (VSIX) zum Bereitstellen der Assembly für die Project-Eigenschaft.  
  
-   Das Debuggen und testen die Project-Eigenschaft.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint und [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Die [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage in der [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] zum Erstellen eines VSIX-Pakets zum Bereitstellen der Erweiterung der Projekt-Eigenschaft. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="create-the-projects"></a>Erstellen Sie die Projekte
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie zwei Projekte erstellen:  
  
- Ein VSIX-Projekt, um das VSIX-Paket zum Bereitstellen der projekterweiterung zu erstellen.  
  
- Ein Klassenbibliotheksprojekt, das die projekterweiterung implementiert.  
  
  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.  
  
3.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Erweiterbarkeit** Knoten.  
  
    > [!NOTE]  
    >  Dieser Knoten ist nur verfügbar, wenn Sie Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework, und wählen Sie dann die **VSIX-Projekt** Vorlage.  
  
5.  In der **Namen** geben **ProjectExtensionPackage**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **ProjectExtensionPackage** -Projekt wird im **Projektmappen-Explorer**.  
  
#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann **Windows**.  
  
3.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework, und wählen Sie dann die **Klassenbibliothek** Projektvorlage.  
  
4.  In der **Namen** geben **ProjectExtension**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **ProjectExtension** -Projekt zur Projektmappe und öffnet die Class1-Codedatei.  
  
5.  Löschen Sie die Class1-Codedatei aus dem Projekt.  
  
## <a name="configure-the-project"></a>Konfigurieren des Projekts
 Bevor Sie Code zum Erstellen der projekterweiterung schreiben, fügen Sie Codedateien und Assemblyverweise das Erweiterungsprojekt.  
  
#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt  
  
1.  Fügen Sie eine Codedatei mit dem Namen **CustomProperty** dem ProjectExtension-Projekt.  
  
2.  Öffnen Sie das Kontextmenü für die **ProjectExtension** Projekt, und wählen Sie dann **Verweis hinzufügen**.  
  
3.  In der **Verweis-Manager - CustomProperty** Dialogfeld auf die **Framework** Knoten, und wählen Sie dann das Kontrollkästchen neben den Assemblys für System.ComponentModel.Composition und "System.Windows.Forms".  
  
4.  Wählen Sie die **Erweiterungen** Knoten, wählen Sie das Kontrollkästchen neben der Microsoft.VisualStudio.SharePoint und EnvDTE-Assembly, und wählen Sie dann die **OK** Schaltfläche.  
  
5.  In **Projektmappen-Explorer**unter der **Verweise** Ordner für die **ProjectExtension** Projekts **EnvDTE**.  
  
6.  In der **Eigenschaften** Ändern der **Embed Interop Types** Eigenschaft **"false"**.  
  
## <a name="define-the-new-sharepoint-project-property"></a>Definieren Sie die neue SharePoint-Projekt-Eigenschaft
 Erstellen Sie eine Klasse, die die projekterweiterung und das Verhalten der neuen Projekteigenschaft definiert. Definieren Sie die neue projekterweiterung, die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle. Implementieren Sie diese Schnittstelle, wenn Sie eine Erweiterung für eine SharePoint-Projekt definieren möchten. Fügen Sie außerdem die <xref:System.ComponentModel.Composition.ExportAttribute> der-Klasse. Mit diesem Attribut können [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ermitteln und Laden Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Implementierung. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Typ, der Konstruktor des Attributs.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Um die neue SharePoint-Projekt-Eigenschaft zu definieren.  
  
1.  Fügen Sie den folgenden Code in die Codedatei "CustomProperty" ein.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="build-the-solution"></a>Erstellen der Projektmappe
 Als Nächstes erstellen Sie die Projektmappe aus, um sicherzustellen, dass es ohne Fehler kompiliert wird.  
  
#### <a name="to-build-the-solution"></a>So erstellen Sie die Projektmappe  
  
1.  Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Erstellen Sie ein VSIX-Paket zum Bereitstellen der Erweiterung der Projekt-Eigenschaft
 Verwenden Sie zum Bereitstellen der projekterweiterung VSIX-Projekt in der Projektmappe, um ein VSIX-Paket zu erstellen. Konfigurieren Sie zuerst das VSIX-Paket, indem Sie die im VSIX-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest" ein, und wählen Sie dann die **öffnen** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Öffnet die Datei im manifest-Designer. Die Informationen, die in angezeigt wird der **Metadaten** Registerkarte auch angezeigt, der **Erweiterungen und Updates**. Alle VSIX-Pakete müssen die Datei "extension.vsixmanifest". Weitere Informationen zu dieser Datei finden Sie unter [Referenz zum VSIX-Erweiterungsschema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  In der **Produktname** geben **Custom Project Property**.  
  
3.  In der **Autor** geben **Contoso**.  
  
4.  In der **Beschreibung** geben **eine benutzerdefinierte SharePoint-Projekt-Eigenschaft, die die Zuordnung der Ressourcenordner des Projekts schaltet**.  
  
5.  Wählen Sie die **Assets** Registerkarte, und wählen Sie dann die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.  
  
6.  In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MEFComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  In der **Quelle** wählen die **ein Projekt in der aktuellen Projektmappe** Optionsfeld aus.  
  
8.  In der **Projekt** wählen **ProjectExtension**.  
  
     Dieser Wert gibt den Namen der Assembly, die Sie in das Projekt erstellen.  
  
9. Wählen Sie **OK** schließen die **neue Anlage hinzufügen** Dialogfeld.  
  
10. Wählen Sie auf der Menüleiste **Datei** > **Alles speichern** Wenn Sie abgeschlossen haben, und schließen Sie dann den Manifesten-Designer.  
  
11. Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe**, und klicken Sie dann stellen Sie sicher, dass das Projekt ohne Fehler kompiliert wird.  
  
12. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ProjectExtensionPackage** Projekt, und wählen die **Ordner in Datei-Explorer öffnen** Schaltfläche.  
  
13. In **Datei-Explorer**Buildausgabeordner für das ProjectExtensionPackage-Projekt öffnen, und stellen Sie sicher, dass der Ordner eine Datei enthält, mit dem Namen ProjectExtensionPackage.vsix.  
  
     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.  
  
## <a name="test-the-project-property"></a>Testen Sie die Project-Eigenschaft
 Sie nun können zum Testen der benutzerdefinierten Eigenschaft. Es ist am einfachsten, Debuggen und testen das neue Projekt eigenschaftenerweiterung in einer experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Diese Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird erstellt, wenn Sie ein VSIX-Projekts oder eines anderen Erweiterbarkeit ausführen. Nachdem Sie das Projekt gedebuggt haben, können Sie die Erweiterung auf Ihrem System installieren und fahren Sie mit dem Debuggen und testen es in einer regulären Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Debuggen und testen die Erweiterung in einer experimentellen Instanz von Visual Studio  
  
1.  Starten Sie neu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit Administratoranmeldeinformationen, und öffnen Sie dann die ProjectExtensionPackage-Lösung.  
  
2.  Starten Sie einen Debugbuild Ihres Projekts entweder durch Auswählen der **F5** -Taste oder wählen Sie auf der Menüleiste die Optionen **Debuggen** > **Debuggen starten**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Erweiterung %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Projekt Property\1.0 und eine experimentelle Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  In der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], erstellen Sie ein SharePoint-Projekt für eine farmlösung und die Standardwerte für die anderen Werte in den Assistenten verwenden.  
  
    1.  Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.  
  
    2.  Am oberen Rand der **neues Projekt** Dialogfeld wählen **.NET Framework 3.5** in der Liste der Versionen von .NET Framework.  
  
         SharePoint-Tools-Erweiterungen erfordern Funktionen für die in dieser Version von der [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  Unter der **Vorlagen** Knoten erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, wählen Sie die **SharePoint** Knoten und wählen Sie dann die **2010** Knoten.  
  
    4.  Wählen Sie die **SharePoint 2010-Projekt** Vorlage, und geben Sie dann **ModuleTest** als den Namen des Projekts.  
  
4.  In **Projektmappen-Explorer**, wählen Sie die **ModuleTest** Projektknoten.  
  
     Eine neue benutzerdefinierte Eigenschaft **Zuordnung für den Ordner "Images"** wird in der **Eigenschaften** Fenster hat den Standardwert des **"false"**.  
  
5.  Ändern Sie den Wert dieser Eigenschaft, um **"true"**.  
  
     Das SharePoint-Projekt wird ein Ressourcenordner hinzugefügt.  
  
6.  Ändern Sie der Wert dieser Eigenschaft zurück, in **"false"**.  
  
     Bei Auswahl der **Ja** Schaltfläche der **löschen Sie den Ordner Bilder?** (Dialogfeld), die Bilder Ressourcenordner aus dem SharePoint-Projekt gelöscht.  
  
7.  Schließen Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Siehe auch
 [Erweitern von SharePoint-Projekte](../sharepoint/extending-sharepoint-projects.md)   
 [Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Konvertieren Sie zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Speichern von Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  

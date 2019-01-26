---
title: Importieren von Elementen aus einer vorhandenen SharePoint-Website | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9dfe79823bbbbb9b96d9732a18272a15c9b3024e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864617"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Importieren von Elementen aus einer vorhandenen SharePoint-Website
  Mit der Projektvorlage „SharePoint-Lösungspaket importieren“ können Sie Elemente wie Inhaltstypen und Felder aus vorhandenen SharePoint-Websites in einer neuen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -SharePoint-Projektmappe wiederverwenden. Obwohl Sie die meisten importierten Projektmappen ohne Änderung ausführen können, müssen bestimmte Einschränkungen und Probleme berücksichtigt werden, insbesondere, wenn Sie Elemente nach deren Import ändern.  
  
> [!NOTE]  
>  Wenn Sie wiederverwendbare Workflows importieren möchten, verwenden Sie die Projektvorlage „Wiederverwendbaren Workflow importieren“. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Richtlinien für das Importieren von wiederverwendbaren Workflows](../sharepoint/guidelines-for-importing-reusable-workflows.md).  
  
## <a name="supported-sharepoint-solutions"></a>Unterstützte SharePoint-Lösungen
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] unterstützt uneingeschränkt das Importieren von Projektmappen, die in [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]erstellt wurden.  
  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] unterstützt nicht das Importieren von Projektmappen, die in den folgenden Anwendungen erstellt wurden:  
  
- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]  
  
- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]  
  
- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]  
  
- Microsoft SharePoint Designer 2007  
  
- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]  
  
  Obwohl Sie Projektmappen, die mit einer dieser Anwendungen erstellt wurden, häufig erfolgreich importieren können, ist diese Funktionalität weder getestet, noch wird sie unterstützt.  
  
## <a name="item-import-restrictions"></a>Den elementimport
 Obwohl die meisten SharePoint-Elemente können, aus einer vorhandenen importiert werden *.wsp* -Datei die folgenden Elemente werden nicht unterstützt und erfordern möglicherweise Änderungen an ordnungsgemäß funktioniert:  
  
- BDC-Entitäten  
  
- Codeworkflow-Zuordnungselemente  
  
- Codeworkflows  
  
- Visuelle Webparts (.ascx)  
  
- Webdienste (*asmx*)  
  
- Inhaltstypbindungen  
  
- Ereignisempfänger  
  
- Listendefinitionen (Vorlagen)  
  
- Websitedefinitionen  
  
  Beim Exportieren einer Lösung aus [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], diese Elemente automatisch ausgeschlossen sind die *.wsp* Datei. Allerdings andere *.wsp* generiert wurden nicht unterstützte Tools können diese Elemente enthalten. (Siehe „Unterstützte SharePoint-Projektmappen (SharePoint-Lösungen)“ weiter oben in diesem Thema.)  
  
## <a name="what-happens-when-you-import-a-solution"></a>Was geschieht, wenn Sie eine Projektmappe importieren
 Wenn Sie eine Projektmappe mit der Vorlage "SharePoint-Lösungspaket importieren" importieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopiert den Inhalt der *.wsp* -Datei und versucht, abzugleichen und beizubehalten, so viele Zuordnungen und Verweise zwischen importiert Elemente und ihre Dateien wie möglich.  
  
 Alle importierten Elemente werden in entsprechende Ordner im **Projektmappen-Explorer**kopiert. Inhaltstypen werden z. B. im Ordner **Inhaltstypen** und Listeninstanzen werden unter **Listeninstanzen**angezeigt. Dateien, die einem importierten Element zugeordnet sind, werden ebenfalls in den Ordner des Elements kopiert. Beispielsweise umfasst eine importierte Listeninstanz ihre Module, Formulare und ASPX-Seiten.  
  
### <a name="dependent-items"></a>Abhängige Elemente
 Wenn Sie im Assistenten „SharePoint-Lösungspaket importieren“ ein Element, aber nicht dessen abhängige Elemente auswählen, werden Sie in einem Meldungsfeld darauf hingewiesen, dass die abhängigen Elemente vor dem Importieren ebenfalls ausgewählt werden müssen.  
  
### <a name="what-are-features"></a>Welche Funktionen sind?
 SharePoint Designer-Benutzer stellen möglicherweise fest, dass unerwartete Dateien, so genannte *Funktionen*, in importierten Projektmappen im **Projektmappen-Explorer** angezeigt werden. Obwohl diese Funktionen bereits in der SharePoint Designer-Projektmappe vorhanden waren, wurden sie in der Ansicht ausgeblendet. Funktionen sind jetzt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]sichtbar.  
  
 Funktionen sind Container für SharePoint-Elemente. Jede Funktion verwaltet einen Verweis auf jedes Element (etwa Inhaltstypen und Listendefinitionen) das sie enthält. Wenn Sie eine Projektmappe importieren, richtet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Funktionen für alle importierten Elemente ein und versucht, die Funktion-zu-Element-Beziehungen für die Dateien beizubehalten. Alle Dateien, deren Verweise nicht aufgelöst werden konnten, werden im Ordner **Andere importierte Dateien** gespeichert.  
  
 Weitere Informationen zu Funktionen finden Sie unter [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md) und [arbeiten mit Features](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
### <a name="handle-special-cases"></a>Besondere Fälle verarbeiten
 In einigen Fällen kann Visual Studio ein Element nicht mit seinen abhängigen Dateien zusammenführen. Alle Dateien, die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nicht auflösen konnte, werden im Ordner **Andere importierte Dateien**angezeigt. Außerdem werden deren **DeploymentType** -Eigenschaften auf **NoDeployment** festgelegt, sodass sie nicht mit der Projektmappe bereitgestellt werden.  
  
 Beispielsweise, wenn Sie die Listendefinition "ExpenseForms" importieren, eine Listendefinition mit diesem Namen wird unter der **Listendefinitionen** Ordner **Projektmappen-Explorer** zusammen mit seiner  *"Elements.xml"* und *"Schema.xml"* Dateien. Allerdings werden die zugeordneten ASPX- und HTML-Formulare ggf. in einem Ordner namens **ExpenseForms** im Ordner **Andere importierte Dateien** angeordnet. Um den Import abzuschließen, verschieben Sie diese Dateien im **Projektmappen-Explorer** in die Listendefinition „ExpenseForms“, und ändern Sie die **DeploymentType** -Eigenschaft für jede Datei von **NoDeployment** in **ElementFile**.  
  
 Beim Importieren von Ereignisempfängern, die *"Elements.xml"* Datei wird auf den richtigen Speicherort kopiert, aber Sie müssen die Assembly manuell in das Projektmappenpaket einschließen, damit sie mit der Lösung bereitgestellt wird. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] wie Sie dies vornehmen können, finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen zusätzlicher Assemblys](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Wenn Sie Workflows importieren, werden InfoPath-Formulare in den Ordner **Andere importierte Dateien** kopiert. Wenn die *.wsp* -Datei enthält eine Webvorlage, wird Sie als Startseite im festgelegt **Projektmappen-Explorer**.  
  
## <a name="import-fields-and-property-bags"></a>Importieren von Feldern und eigenschaftenbehältern
 Wenn Sie eine Projektmappe, die mehrere Felder hat importieren, werden alle separaten Felddefinitionen in einem einzigen zusammengeführt *"Elements.xml"* Datei unter einem Knoten im **Projektmappen-Explorer** namens **Felder** . Auf ähnliche Weise werden alle eigenschaftenbehältereinträge zusammengeführt, in eine *"Elements.xml"* Datei in einem Knoten namens **PropertyBags**.  
  
 Felder in SharePoint sind Spalten mit einem angegebenen Datentyp, z. B. „Text“, „Boolesch“ oder „Nachschlagen“. Weitere Informationen finden Sie unter [Baustein: Spalten und Feldtypen](http://go.microsoft.com/fwlink/?LinkId=182304). Mithilfe von Eigenschaftenbehältern können Sie Eigenschaften zu Objekten in SharePoint hinzufügen, wobei alles von einer Farm bis zu einer Liste auf einer SharePoint-Website möglich ist. Eigenschaftenbehälter sind als Hashtabelle mit Eigenschaftennamen und -werten implementiert. Weitere Informationen finden Sie unter [Verwalten der SharePoint-Konfiguration](http://go.microsoft.com/fwlink/?LinkId=182296) oder [SharePoint Property Bag Settings](http://go.microsoft.com/fwlink/?LinkId=182297).  
  
## <a name="delete-items-in-the-project"></a>Löschen von Elementen im Projekt
 Die meisten Elemente in SharePoint-Projektmappen haben mindestens ein abhängiges Element. Listeninstanzen sind z. B. von Inhaltstypen abhängig, und Inhaltstypen sind von Feldern abhängig. Nachdem Sie eine SharePoint-Projektmappe importiert haben, gibt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , wenn Sie ein Element, nicht aber dessen abhängige Elemente in der Projektmappe gelöscht haben, erst dann eine Benachrichtigungen zu Verweisproblemen aus, wenn Sie versuchen, die Projektmappe bereitzustellen. Wenn eine importierte Projektmappe beispielsweise eine Listeninstanz beinhaltet, die von einem Inhaltstyp abhängt, und Sie diesen Inhaltstyp löschen, kann bei der Bereitstellung ein Fehler auftreten. Der Fehler tritt auf, wenn das abhängige Element auf dem SharePoint-Server nicht vorhanden ist. Auf ähnliche Weise, wenn ein gelöschtes Element einen zugehörigen Eigenschaftenbehälter hat, löschen Sie diese eigenschaftenbehältereinträge aus der **PropertyBags** *"Elements.xml"* Datei. Daher empfiehlt es sich, wenn Sie Elemente aus einer importierten Projektmappe löschen und dann Bereitstellungsfehler auftreten, dass Sie überprüfen, ob es abhängige Elementen gibt, die ebenfalls gelöscht werden müssen.  
  
## <a name="restore-missing-feature-attributes"></a>Wiederherstellen von fehlenden Funktionsattributen
 Wenn Projektmappen importiert werden, werden einige optionale Funktionsattribute (Featureattribute) aus dem importierten Funktionsmanifest nicht übernommen. Wenn Sie diese Attribute in der neuen Funktionsdatei wiederherstellen möchten, ermitteln Sie die fehlenden Attribute, durch die ursprüngliche Funktionsdatei mit dem neuen Funktionsmanifest vergleichen, und befolgen Sie die Anweisungen im Thema [Vorgehensweise: Anpassen eines SharePoint-Features](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Erkennung von Bereitstellungskonflikten wird für integrierte Listeninstanzen nicht ausgeführt.
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] führt keine Erkennung von Bereitstellungskonflikten für integrierte Listeninstanzen (dies sind die Standardlisteninstanzen, die mit SharePoint geliefert werden) aus. Die Konflikterkennung wird nicht ausgeführt, damit verhindert wird, dass die integrierten Listeninstanzen in SharePoint überschrieben werden. Die integrierten Listeninstanzen werden weiterhin bereitgestellt bzw. aktualisiert, werden aber niemals gelöscht oder überschrieben. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Problembehandlung bei SharePoint-Packen und-Bereitstellen](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="import-sharepoint-server-2010-workflows"></a>Importieren von SharePoint Server 2010-workflows
 Wenn Sie einen in [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]erstellten Workflow importieren, wird dieser nach der Bereitstellung nicht ordnungsgemäß ausgeführt. Der Workflow wird nicht ordnungsgemäß ausgeführt, da bestimmte Assemblys fehlen und  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] -Workflows InfoPath-Formulare enthalten, die in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Workflowprojektmappen derzeit nicht unterstützt werden. Importierte [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] -Workflows können jedoch ordnungsgemäß ausgeführt werden, nachdem Sie bestimmte Elemente korrigiert haben, so z. B. Hinzufügen von Verweisen auf die [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] -Assemblys und erneutes Verbinden der InfoPath-Formulare. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Importieren von SharePoint Server 2010-Workflows](http://go.microsoft.com/fwlink/?LinkId=182226).  
  
## <a name="item-name-character-limit"></a>Maximale Länge von Element
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hat für Projekt- und Projektelementnamen samt Pfad eine maximale Länge von 260 Zeichen. Wenn Sie eine Projektmappe importieren und ein Elementname diese Grenze überschreitet, wird folgender Fehler angezeigt:  
  
 **Der angegebene Pfad und/oder Dateiname sind zu lang. Der vollqualifizierte Dateiname muss weniger als 260 Zeichen umfassen, und der Verzeichnisname muss kürzer als 248 Zeichen sein.**  
  
 Wenn dieser Fehler auftritt, wird das Element nicht erstellt. Dieses Problem tritt am häufigsten bei importierten Modulen auf. Um dieses Problem zu vermeiden, gehen Sie wie folgt vor:  
  
-   Geben Sie kurze Namen für das Projekt im Dialogfeld **Neues Projekt hinzufügen** ein.  
  
-   Erstellen Sie das Projekt in einem Speicherort möglichst nahe am Stammordner, um den Pfad kurz zu halten.  
  
## <a name="the-sharepointproductversion-attribute"></a>SharePointProductVersion-Attribut
 Wenn Sie eine in einer früheren Version von SharePoint, etwa [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] oder [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], erstellte Projektmappe importieren, ändern Sie entweder den Wert des SharePointProductVersion-Attributs im Paketmanifest in 12.0, oder fügen Sie ein Skript-Manager-Steuerelement in alle importierten Webseiten ein, und belassen Sie die SharePointProductVersion auf 14.0. Andernfalls werden importierte Web Forms (Webformulare) nicht in SharePoint angezeigt.  
  
### <a name="background"></a>Hintergrund  
 Projektmappen in [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] enthalten ein Attribut namens SharePointProductVersion. SharePoint verwendet dieses Attribut in seinen Paketmanifesten, um die SharePoint-Version zu bestimmen, für die die Projektmappe entworfen wurde. Die beiden gültigen Werte sind 12.0 und 14.0. Der Wert 12.0 gibt an, dass das Element für [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] oder [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]entworfen wurde, der Wert 14.0 gibt an, dass das Element für [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]entworfen wurde.  
  
 Für erhöhte Sicherheit beim Rendern von ASPX-Seiten erfordern [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] und [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , dass alle ASPX-Seiten oder Gestaltungsvorlagen ein Skript-Manager-Steuerelement enthalten. Weitere Informationen zum Skript-Manager finden Sie unter [Übersicht über das ScriptManager-Steuerelement](http://go.microsoft.com/fwlink/?LinkID=169399). Weil das Skript-Manager-Steuerelement in [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] und [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]nicht verfügbar ist, muss jeder [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] - oder [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] -Seite, die auf [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]aktualisiert wird, ein solches Steuerelement hinzugefügt werden. Für ASPX-Seiten, für die eine Standardgestaltungsvorlage verwendet wird, ist kein Skript-Manager-Steuerelement erforderlich, da der Standardgestaltungsvorlage bereits ein solches Steuerelement hinzugefügt wurde. ASPX-Seiten, für die keine Gestaltungsvorlage oder eine benutzerdefinierte Gestaltungsvorlage verwendet wird, muss jedoch ein Skript-Manager-Steuerelement hinzugefügt werden, damit sie in [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]funktionieren.  
  
 Das Fehlen eines Skript-Manager-Steuerelements kann ein Problem darstellen, wenn Sie ein [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] - oder ein [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] -Projekt in [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]importieren, da das SharePointProductVersion-Attribut aller neuen Projekte auf 14.0 festgelegt wird. Wenn Sie ein aktualisiertes Projekt bereitstellen, das ein Webformular ohne Skript-Manager hat, wird das Formular in SharePoint nicht angezeigt.  
  
## <a name="see-also"></a>Siehe auch
 [Exemplarische Vorgehensweise: Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)   
 [Richtlinien für das Importieren von wiederverwendbaren workflows](../sharepoint/guidelines-for-importing-reusable-workflows.md)   
 [Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)   
 [Vorgehensweise: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)  

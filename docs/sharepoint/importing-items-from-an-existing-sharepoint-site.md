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
ms.openlocfilehash: 820e7c6f2ac7ea3e65e2156f33464bec96fce091
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982590"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Importieren von Elementen aus einer vorhandenen SharePoint-Website
  Mit der Projektvorlage „SharePoint-Lösungspaket importieren“ können Sie Elemente wie Inhaltstypen und Felder aus vorhandenen SharePoint-Websites in einer neuen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -SharePoint-Projektmappe wiederverwenden. Obwohl Sie die meisten importierten Projektmappen ohne Änderung ausführen können, müssen bestimmte Einschränkungen und Probleme berücksichtigt werden, insbesondere, wenn Sie Elemente nach deren Import ändern.

> [!NOTE]
> Wenn Sie wiederverwendbare Workflows importieren möchten, verwenden Sie die Projektvorlage „Wiederverwendbaren Workflow importieren“. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Richtlinien für den Import wiederverwendbarer Workflows](../sharepoint/guidelines-for-importing-reusable-workflows.md).

## <a name="supported-sharepoint-solutions"></a>Unterstützte SharePoint-Lösungen
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] unterstützt uneingeschränkt das Importieren von Projektmappen, die in [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]erstellt wurden.

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] unterstützt nicht das Importieren von Projektmappen, die in den folgenden Anwendungen erstellt wurden:

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint Designer 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  Obwohl Sie Projektmappen, die mit einer dieser Anwendungen erstellt wurden, häufig erfolgreich importieren können, ist diese Funktionalität weder getestet, noch wird sie unterstützt.

## <a name="item-import-restrictions"></a>Einschränkungen für den Element Import
 Obwohl die meisten SharePoint-Elemente aus einer vorhandenen *wsp* -Datei importiert werden können, werden die folgenden Elemente nicht unterstützt und müssen möglicherweise geändert werden, damit Sie ordnungsgemäß funktionieren:

- BDC-Entitäten

- Codeworkflow-Zuordnungselemente

- Codeworkflows

- Visuelle Webparts (.ascx)

- Webdienste ( *. asmx*)

- Inhaltstypbindungen

- Ereignisempfänger

- Listendefinitionen (Vorlagen)

- Websitedefinitionen

  Wenn Sie eine Projekt Mappe aus [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]exportieren, werden diese Elemente automatisch aus der *wsp* -Datei ausgeschlossen. Andere *. wsp* -Dateien, die von nicht unterstützten Tools generiert werden, können diese Elemente jedoch enthalten. (Siehe „Unterstützte SharePoint-Projektmappen (SharePoint-Lösungen)“ weiter oben in diesem Thema.)

## <a name="what-happens-when-you-import-a-solution"></a>Was geschieht beim Importieren einer Projekt Mappe?
 Wenn Sie eine Projekt Mappe mit der Vorlage "SharePoint-Lösungspaket importieren" importieren, kopiert [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] den gesamten Inhalt der *wsp* -Datei und versucht, so viele Zuordnungen und Verweise zwischen importierten Elementen und deren Dateien abzugleichen und beizubehalten. man.

 Alle importierten Elemente werden in entsprechende Ordner im **Projektmappen-Explorer**kopiert. Inhaltstypen werden z. B. im Ordner **Inhaltstypen** und Listeninstanzen werden unter **Listeninstanzen**angezeigt. Dateien, die einem importierten Element zugeordnet sind, werden ebenfalls in den Ordner des Elements kopiert. Beispielsweise umfasst eine importierte Listeninstanz ihre Module, Formulare und ASPX-Seiten.

### <a name="dependent-items"></a>Abhängige Elemente
 Wenn Sie im Assistenten „SharePoint-Lösungspaket importieren“ ein Element, aber nicht dessen abhängige Elemente auswählen, werden Sie in einem Meldungsfeld darauf hingewiesen, dass die abhängigen Elemente vor dem Importieren ebenfalls ausgewählt werden müssen.

### <a name="what-are-features"></a>Was sind Features?
 SharePoint Designer-Benutzer stellen möglicherweise fest, dass unerwartete Dateien, so genannte *Funktionen*, in importierten Projektmappen im **Projektmappen-Explorer** angezeigt werden. Obwohl diese Funktionen bereits in der SharePoint Designer-Projektmappe vorhanden waren, wurden sie in der Ansicht ausgeblendet. Funktionen sind jetzt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]sichtbar.

 Funktionen sind Container für SharePoint-Elemente. Jede Funktion verwaltet einen Verweis auf jedes Element (etwa Inhaltstypen und Listendefinitionen) das sie enthält. Wenn Sie eine Projektmappe importieren, richtet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Funktionen für alle importierten Elemente ein und versucht, die Funktion-zu-Element-Beziehungen für die Dateien beizubehalten. Alle Dateien, deren Verweise nicht aufgelöst werden konnten, werden im Ordner **Andere importierte Dateien** gespeichert.

 Weitere Informationen zu-Funktionen finden Sie unter [entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md) und [Arbeiten mit Funktionen](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

### <a name="handle-special-cases"></a>Behandeln von Sonderfällen
 In einigen Fällen kann Visual Studio ein Element nicht mit seinen abhängigen Dateien zusammenführen. Alle Dateien, die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nicht auflösen konnte, werden im Ordner **Andere importierte Dateien**angezeigt. Außerdem werden deren **DeploymentType** -Eigenschaften auf **NoDeployment** festgelegt, sodass sie nicht mit der Projektmappe bereitgestellt werden.

 Wenn Sie z. b. die Listen Definition "expenseforms" importieren, wird eine Listen Definition mit diesem Namen in **Projektmappen-Explorer** zusammen mit den Dateien " *Elements. XML* " und " *Schema. XML* " unter dem Ordner **Listen Definitionen** angezeigt. Allerdings werden die zugeordneten ASPX- und HTML-Formulare ggf. in einem Ordner namens **ExpenseForms** im Ordner **Andere importierte Dateien** angeordnet. Um den Import abzuschließen, verschieben Sie diese Dateien im **Projektmappen-Explorer** in die Listendefinition „ExpenseForms“, und ändern Sie die **DeploymentType** -Eigenschaft für jede Datei von **NoDeployment** in **ElementFile**.

 Wenn Sie Ereignis Empfänger importieren, wird die Datei " *Elements. XML* " in den richtigen Speicherort kopiert, aber Sie müssen die Assembly manuell in das Projektmappenpaket einschließen, damit Sie mit der Lösung bereitgestellt wird. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] Vorgehensweise finden Sie unter Gewusst [wie: Hinzufügen und Entfernen zusätzlicher](../sharepoint/how-to-add-and-remove-additional-assemblies.md)Assemblys.

 Wenn Sie Workflows importieren, werden InfoPath-Formulare in den Ordner **Andere importierte Dateien** kopiert. Wenn die *wsp* -Datei eine Webvorlage enthält, wird Sie in **Projektmappen-Explorer**als Startseite festgelegt.

## <a name="import-fields-and-property-bags"></a>Importieren von Feldern und Eigenschaften Säcken
 Wenn Sie eine Projekt Mappe importieren, die mehrere Felder enthält, werden alle separaten Feld Definitionen in einer einzelnen " *Elements. XML* "-Datei unter einem Knoten in **Projektmappen-Explorer** namens **Felder**zusammengeführt. Ebenso werden alle Eigenschaften Behälter Einträge in der Datei " *Elements. XML* " unter einem Knoten namens " **PropertyBag**" zusammengeführt.

 Felder in SharePoint sind Spalten mit einem angegebenen Datentyp, z. B. „Text“, „Boolesch“ oder „Nachschlagen“. Weitere Informationen finden Sie unter [Baustein: Spalten und Feldtypen](/previous-versions/office/developer/sharepoint-2010/ee535893(v=office.14)). Mithilfe von Eigenschaftenbehältern können Sie Eigenschaften zu Objekten in SharePoint hinzufügen, wobei alles von einer Farm bis zu einer Liste auf einer SharePoint-Website möglich ist. Eigenschaftenbehälter sind als Hashtabelle mit Eigenschaftennamen und -werten implementiert. Weitere Informationen finden Sie unter [Verwalten der SharePoint-Konfiguration](/previous-versions/msp-n-p/ff647766(v=pandp.10)) oder [SharePoint Property Bag Settings](https://archive.codeplex.com/?p=pbs).

## <a name="delete-items-in-the-project"></a>Löschen von Elementen im Projekt
 Die meisten Elemente in SharePoint-Projektmappen haben mindestens ein abhängiges Element. Listeninstanzen sind z. B. von Inhaltstypen abhängig, und Inhaltstypen sind von Feldern abhängig. Nachdem Sie eine SharePoint-Projektmappe importiert haben, gibt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , wenn Sie ein Element, nicht aber dessen abhängige Elemente in der Projektmappe gelöscht haben, erst dann eine Benachrichtigungen zu Verweisproblemen aus, wenn Sie versuchen, die Projektmappe bereitzustellen. Wenn eine importierte Projektmappe beispielsweise eine Listeninstanz beinhaltet, die von einem Inhaltstyp abhängt, und Sie diesen Inhaltstyp löschen, kann bei der Bereitstellung ein Fehler auftreten. Der Fehler tritt auf, wenn das abhängige Element auf dem SharePoint-Server nicht vorhanden ist. Wenn ein gelöschtes Element auch über einen zugehörigen Eigenschaften Behälter verfügt, löschen Sie diese Eigenschaften Behälter Einträge in der Datei **PropertyBag** *Elements. XML* . Daher empfiehlt es sich, wenn Sie Elemente aus einer importierten Projektmappe löschen und dann Bereitstellungsfehler auftreten, dass Sie überprüfen, ob es abhängige Elementen gibt, die ebenfalls gelöscht werden müssen.

## <a name="restore-missing-feature-attributes"></a>Fehlende Funktions Attribute wiederherstellen
 Wenn Projektmappen importiert werden, werden einige optionale Funktionsattribute (Featureattribute) aus dem importierten Funktionsmanifest nicht übernommen. Wenn Sie diese Attribute in der neuen Funktions Datei wiederherstellen möchten, ermitteln Sie die fehlenden Attribute, indem Sie die ursprüngliche Funktions Datei mit dem neuen Funktions Manifest vergleichen, und befolgen Sie die Anweisungen im Thema Gewusst [wie: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md).

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Die Erkennung von Bereitstellungs Konflikten wird für integrierte Listen Instanzen nicht durchgeführt.
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] führt keine Erkennung von Bereitstellungskonflikten für integrierte Listeninstanzen (dies sind die Standardlisteninstanzen, die mit SharePoint geliefert werden) aus. Die Konflikterkennung wird nicht ausgeführt, damit verhindert wird, dass die integrierten Listeninstanzen in SharePoint überschrieben werden. Die integrierten Listeninstanzen werden weiterhin bereitgestellt bzw. aktualisiert, werden aber niemals gelöscht oder überschrieben. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] Problembehandlung bei der [SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)

## <a name="import-sharepoint-server-2010-workflows"></a>Importieren von SharePoint Server 2010-Workflows
 Wenn Sie einen in [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]erstellten Workflow importieren, wird dieser nach der Bereitstellung nicht ordnungsgemäß ausgeführt. Der Workflow wird nicht ordnungsgemäß ausgeführt, da bestimmte Assemblys fehlen und  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] -Workflows InfoPath-Formulare enthalten, die in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Workflowprojektmappen derzeit nicht unterstützt werden. Importierte [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] -Workflows können jedoch ordnungsgemäß ausgeführt werden, nachdem Sie bestimmte Elemente korrigiert haben, so z. B. Hinzufügen von Verweisen auf die [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] -Assemblys und erneutes Verbinden der InfoPath-Formulare. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Importieren von SharePoint Server 2010-Workflows](/sharepoint/dev/).

## <a name="item-name-character-limit"></a>Zeichenlimit für Elementnamen
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hat für Projekt- und Projektelementnamen samt Pfad eine maximale Länge von 260 Zeichen. Wenn Sie eine Projektmappe importieren und ein Elementname diese Grenze überschreitet, wird folgender Fehler angezeigt:

 **Der angegebene Pfad, der Dateiname oder beide sind zu lang. Der voll qualifizierte Dateiname muss weniger als 260 Zeichen umfassen, und der Verzeichnisname muss weniger als 248 Zeichen umfassen.**

 Wenn dieser Fehler auftritt, wird das Element nicht erstellt. Dieses Problem tritt am häufigsten bei importierten Modulen auf. Um dieses Problem zu vermeiden, gehen Sie wie folgt vor:

- Geben Sie kurze Namen für das Projekt im Dialogfeld **Neues Projekt hinzufügen** ein.

- Erstellen Sie das Projekt in einem Speicherort möglichst nahe am Stammordner, um den Pfad kurz zu halten.

## <a name="the-sharepointproductversion-attribute"></a>Das sharepointproductversion-Attribut
 Wenn Sie eine in einer früheren Version von SharePoint, etwa [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] oder [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], erstellte Projektmappe importieren, ändern Sie entweder den Wert des SharePointProductVersion-Attributs im Paketmanifest in 12.0, oder fügen Sie ein Skript-Manager-Steuerelement in alle importierten Webseiten ein, und belassen Sie die SharePointProductVersion auf 14.0. Andernfalls werden importierte Web Forms (Webformulare) nicht in SharePoint angezeigt.

### <a name="background"></a>Hintergrund
 Projektmappen in [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] enthalten ein Attribut namens SharePointProductVersion. SharePoint verwendet dieses Attribut in seinen Paketmanifesten, um die SharePoint-Version zu bestimmen, für die die Projektmappe entworfen wurde. Die beiden gültigen Werte sind 12.0 und 14.0. Der Wert 12.0 gibt an, dass das Element für [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] oder [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]entworfen wurde, der Wert 14.0 gibt an, dass das Element für [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]entworfen wurde.

 Für erhöhte Sicherheit beim Rendern von ASPX-Seiten erfordern [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] und [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , dass alle ASPX-Seiten oder Gestaltungsvorlagen ein Skript-Manager-Steuerelement enthalten. Weitere Informationen zum Skript-Manager finden Sie unter [Übersicht über das ScriptManager-Steuerelement](/previous-versions/bb398863(v=vs.140)). Weil das Skript-Manager-Steuerelement in [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] und [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]nicht verfügbar ist, muss jeder [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] - oder [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] -Seite, die auf [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]aktualisiert wird, ein solches Steuerelement hinzugefügt werden. Für ASPX-Seiten, für die eine Standardgestaltungsvorlage verwendet wird, ist kein Skript-Manager-Steuerelement erforderlich, da der Standardgestaltungsvorlage bereits ein solches Steuerelement hinzugefügt wurde. ASPX-Seiten, für die keine Gestaltungsvorlage oder eine benutzerdefinierte Gestaltungsvorlage verwendet wird, muss jedoch ein Skript-Manager-Steuerelement hinzugefügt werden, damit sie in [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] oder [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]funktionieren.

 Das Fehlen eines Skript-Manager-Steuerelements kann ein Problem darstellen, wenn Sie ein [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] - oder ein [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] -Projekt in [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]importieren, da das SharePointProductVersion-Attribut aller neuen Projekte auf 14.0 festgelegt wird. Wenn Sie ein aktualisiertes Projekt bereitstellen, das ein Webformular ohne Skript-Manager hat, wird das Formular in SharePoint nicht angezeigt.

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [Richtlinien zum Importieren wiederverwendbarer Workflows](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows in SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [Vorgehensweise: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)

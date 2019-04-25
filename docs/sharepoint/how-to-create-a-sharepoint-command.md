---
title: 'Vorgehensweise: Erstellen Sie ein SharePoint-Befehl | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 49d253b63b682d81903003d6bdd148922989f274
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082320"
---
# <a name="how-to-create-a-sharepoint-command"></a>Vorgehensweise: Erstellen eines SharePoint-Befehls
  Wenn Sie das Serverobjektmodell in einer SharePoint-Tools-Erweiterung verwenden möchten, müssen Sie erstellen eine benutzerdefinierte *SharePoint-Befehls* zum Aufrufen der API. Sie definieren den SharePoint-Befehl in einer Assembly, die direkt in das Serverobjektmodell aufrufen können.

 Weitere Informationen zum Zweck der SharePoint-Befehle finden Sie unter [rufen Sie in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>So erstellen Sie einen SharePoint-Befehl

1. Erstellen Sie ein Klassenbibliotheksprojekt, das die folgende Konfiguration aufweist:

    - Ist .NET Framework 3.5 ausgerichtet. Weitere Informationen zur Auswahl des Zielframeworks finden Sie unter [Vorgehensweise: Erstellen von Projekten für eine bestimmte .NET Framework-Version](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

    - Das Ziel ist die "anycpu" oder X64 Plattform. Standardmäßig ist die Zielplattform für Klassenbibliotheksprojekte "anycpu". Weitere Informationen zum Auswählen der Zielplattform finden Sie unter [Vorgehensweise: Konfigurieren von Projekten für Zielplattformen](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    >  Einen SharePoint-Befehl kann nicht im selben Projekt, das eine SharePoint-Tools-Erweiterung definiert implementiert werden, da SharePoint-Befehle das Ziel .NET Framework 3.5 und SharePoint-Tools-Erweiterungen als Ziel der [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Sie müssen alle SharePoint-Befehle definieren, die durch die Erweiterung in einem separaten Projekt verwendet werden. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.SharePoint.Commands

    - Microsoft.SharePoint

3. Erstellen Sie eine Methode, die Ihre SharePoint-Befehl definiert, in einer Klasse im Projekt. Die Methode muss die folgenden Richtlinien entsprechen:

    - Sie können einen oder zwei Parameter haben.

         Der erste Parameter muss ein <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> Objekt. Dieses Objekt stellt die Microsoft.SharePoint.SPSite oder Microsoft.SharePoint.SPWeb, in dem der Befehl ausgeführt wird. Außerdem wird ein <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> -Objekt, das zum Schreiben von Nachrichten verwendet werden kann die **Ausgabe** Fenster oder **Fehlerliste** Fenster in Visual Studio.

         Der zweite Parameter kann ein Typ Ihrer Wahl sein, aber dieser Parameter ist optional. Sie können diesen Parameter auf der SharePoint-Befehl hinzufügen, Daten aus der SharePoint-Tools-Erweiterung an den Befehl übergeben werden sollen.

    - Sie können einen Rückgabewert haben, aber dies ist optional.

    - Der zweite Parameter und Rückgabetypen-Wert muss ein Typ sein, der von der Windows Communication Foundation (WCF) serialisiert werden können. Weitere Informationen finden Sie unter [Types Supported by the Data Contract Serializer](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) und [mithilfe der XmlSerializer-Klasse](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - Die Methode kann eine beliebige Sichtbarkeit aufweisen (**öffentliche**, **interne**, oder **private**), und es kann statisch oder nicht statisch sein.

4. Anwenden der <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> an die Methode. Dieses Attribut gibt einen eindeutigen Bezeichner für den Befehl an; Diese ID muss nicht dem Methodennamen entsprechen.

     Sie müssen den gleichen Bezeichner angeben, wenn Sie den Befehl aufrufen, die sich von der SharePoint-Tools-Erweiterung. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen einer SharePoint-Befehls](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, einen SharePoint-Befehl mit dem Bezeichner `Contoso.Commands.UpgradeSolution`. Dieser Befehl verwendet die APIs in das Serverobjektmodell auf einer bereitgestellten Lösung aktualisieren.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 Zusätzlich zu den impliziten ersten <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> -Parameter mit diesem Befehl verfügt auch über eine benutzerdefinierte Zeichenfolge-Parameter, der den vollständigen Pfad der WSP-Datei enthält, die zur SharePoint-Website aktualisiert wird. Dieser Code im Rahmen eines größeren Beispiels, finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint.Commands

- Microsoft.SharePoint

## <a name="deploying-the-command"></a>Bereitstellen des Befehls
 Zum Bereitstellen des Befehls, schließen Sie die Befehlsassembly in der gleichen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterung (*Vsix*) Paket mit der Erweiterungsassembly, die der Befehl verwendet. Sie müssen auch einen Eintrag für die Befehlsassembly "in der Datei" extension.vsixmanifest "hinzufügen. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
- [Rufen Sie in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Vorgehensweise: Führen Sie einen SharePoint-Befehl](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

---
title: Erweitern von SharePoint-Projekten | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6bc92d65ed179c7f2cb2f569a7d254a025887845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967480"
---
# <a name="extend-sharepoint-projects"></a>Erweitern von SharePoint-Projekten
  Erstellen Sie eine Projekt Erweiterung, wenn Sie Features auf Projektebene von SharePoint-Projekten anpassen möchten. Beispielsweise können Sie benutzerdefinierte Projekteigenschaften hinzufügen oder auf Ereignisse auf Projektebene reagieren, die ausgelöst werden, wenn der Benutzer eine SharePoint-Projekt Mappe in Visual Studio entwickelt.

## <a name="create-project-extensions"></a>Erstellen von Projekt Erweiterungen
 Um ein Projekt Element zu erweitern, erstellen Sie eine Visual Studio-Erweiterungsassembly, die die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle implementiert. Weitere Informationen finden Sie unter Vorgehens [Weise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Wenn Sie eine Projekt Erweiterung erstellen, können Sie den SharePoint-Projekten auch die folgenden Funktionen hinzufügen:

- Fügen Sie ein Kontextmenü Element hinzu. Das Menü Element wird angezeigt, wenn Sie das Kontextmenü für einen SharePoint-Projekt Knoten in **Projektmappen-Explorer** öffnen, indem Sie mit der rechten Maustaste auf den Knoten klicken oder ihn auswählen und **dann die** + Taste**F10** drücken. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Kontextmenü Elements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Fügen Sie eine benutzerdefinierte Eigenschaft hinzu. Die-Eigenschaft wird im **Eigenschaften** Fenster angezeigt, wenn Sie ein SharePoint-Projekt in **Projektmappen-Explorer**auswählen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Eine exemplarische Vorgehensweise, die veranschaulicht, wie eine Projekt Erweiterung erstellt, bereitgestellt und getestet wird, finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Verstehen der Beziehung zwischen Projekt Erweiterungen und Projekt Instanzen
 Wenn Sie eine Projekt Erweiterung erstellen, wird die Erweiterung geladen, wenn eine beliebige Art von SharePoint-Projekt in geöffnet wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umfasst mehrere SharePoint-Projektvorlagen, z. b. Listen Definitionen, Inhaltstypen und Ereignis Empfänger. Es gibt jedoch nur einen SharePoint-Projekttyp. Die Projekttypen, die im Dialogfeld **Neues Projekt** angezeigt werden, sind nur Vorlagen, mit denen ein oder mehrere SharePoint-Projekt Elemente gebündelt werden. Da nur ein SharePoint-Projekttyp vorhanden ist, gelten für ein Projekt erstellte Erweiterungen für alle SharePoint-Projekte. Es ist beispielsweise nicht möglich, eine Erweiterung zu erstellen, die nur für ein **Inhaltstyp** Projekt gilt.

 Um auf eine bestimmte Projekt Instanz zuzugreifen, behandeln Sie eines der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> Ereignisse des *ProjectService* -Parameters in der Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> Methode. Um z. b. zu ermitteln, wann ein SharePoint-Projekt zu einer Projekt Mappe hinzugefügt wird, behandeln Sie das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> Ereignis. Weitere Informationen finden Sie unter Vorgehens [Weise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Gewusst wie: Hinzufügen eines Kontextmenü Elements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md)
- [Erweiterte SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Erweitern des SharePoint-Projekt Systems](../sharepoint/extending-the-sharepoint-project-system.md)
